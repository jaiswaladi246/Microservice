pipeline {
    agent any

    options {
        timeout(time: 30, unit: 'MINUTES') // Increase timeout for the entire pipeline
    }

    stages {
        stage('Build & Tag Docker Image') {
            options {
                timeout(time: 10, unit: 'MINUTES') // Increase timeout for this stage
            }
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker build -t chakri2431/microservice/adservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            options {
                timeout(time: 10, unit: 'MINUTES') // Increase timeout for this stage
            }
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker push chakri2431/microservice/adservice:latest "
                    }
                }
            }
        }
    }
}
