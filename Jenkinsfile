#!/usr/bin/env groovy
pipeline {
    agent any

    stages {
	    stage('Setup') {
            steps {
                git url:'http://10.250.10.2:8929/root/trivy.git', branch: ' project'
            }
        }
        stage('Trivy') {
            steps {
                sh 'trivy filesystem --format json --output trivy-result-proyect.json hello-nodejs-testing/'
            }
            post {
                always {
                    recordIssues enabledForFailure: true, tool: trivy(pattern: '*.json')
                }
            }
        }      
        
    }
}
