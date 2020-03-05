#!/bin/env groovy

pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            when {
                expression { env.BRANCH_NAME == 'master' }
            }
            steps {
                configFileProvider([configFile(fileId: 'MySettings', variable: 'MAVEN_SETTINGS_XML')]) {
                  sh 'mvn -U --batch-mode -s $MAVEN_SETTINGS_XML deploy -DskipTests'
                }
                //sh 'mvn deploy -DskipTests'
            }
        }
    }
}
