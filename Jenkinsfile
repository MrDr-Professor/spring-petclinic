#!/bin/env groovy

pipeline {
    agent any

    parameters {
        choice(
            choices: ['master'],
            description: '',
            name: 'BRANCH_NAME')
    }
    
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
        //    when {
        //        expression { params.BRANCH_NAME == 'master' }
        //    }
            steps {
        //        sh 'mvn deploy -DskipTests'
                echo params.BRANCH_NAME
            }
        }
    }
}
