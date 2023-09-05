#!/usr/bin/env groovy

node {
	stage('checkout') {
		checkout scm
	}
	stage('Clean') {
		withMaven(maven: 'maven') {
			if(isUnix()) {
 				sh "mvn clean" 
			} else { 
 				bat "mvn clean" 
			} 			
		}
	}
	stage('backend tests') {
		withMaven(maven: 'maven') {
			if(isUnix()) {
 				sh "mvn clean test" 
			} else { 
 				bat "mvn clean test" 
			} 
		}
	}

	stage('Package') {
		withMaven(maven: 'maven') {
			if(isUnix()) {
 				sh "mvn package -DskipTest" 
			} else { 
 				bat "mvn package -DskipTest" 
			} 
		}
	}

	stage('Build Docker Image') {
		withMaven(maven: 'maven') {
			if(isUnix()) {
 				sh "mvn jib:build" 
			} else { 
 				bat "mvn jib:build" 
			} 
		}
	}

}
