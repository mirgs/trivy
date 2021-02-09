#!/usr/bin/env groovy
pipeline {
    agent any

    stages {
	/*stage('Setup') {
            steps {
                git url:'http://10.250.10.2:8929/root/trivy.git', branch: 'master'
            }
        } */
        stage('Trivy') {
            steps {
                sh 'trivy image --format json --output trivy-results.json debian:10.8'
            }
            post {
                always {
                    recordIssues enabledForFailure: true, tool: trivy(pattern: '*.json')
                }
            }
        }      
        
    }
}
