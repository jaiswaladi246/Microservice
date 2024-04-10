pipeline {
    agent any

    options {
        timeout(time: 30, unit: 'MINUTES') // Increase timeout for the entire pipeline
    }

    stages {
        stage('Build & Tag Docker Image') {
            options {
                timeout(time: 15, unit: 'MINUTES') // Increase timeout for this stage
            }
            steps {
                script {
                    try {
                        withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                            sh "docker build -t chakri2431/microservice/adservice:latest ."
                        }
                    } catch (Exception e) {
                        // Handle build failure
                        currentBuild.result = 'FAILURE'
                        error("Failed to build Docker image: ${e.message}")
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
                    try {
                        withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                            sh "docker push chakri2431/microservice/adservice:latest"
                        }
                    } catch (Exception e) {
                        // Handle push failure
                        currentBuild.result = 'FAILURE'
                        error("Failed to push Docker image: ${e.message}")
                    }
                }
            }
        }
    }
}
