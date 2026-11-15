
pipeline {
    agent any

    environment {
        KUBECONFIG = '/var/lib/jenkins/.kube/config'
    }

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                sh '''
                    kubectl create namespace webapps \
                      --dry-run=client -o yaml | kubectl apply -f -

                    kubectl apply -n webapps -f deployment-service.yml
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                sh '''
                    kubectl get deployments -n webapps
                    kubectl get pods -n webapps
                    kubectl get svc -n webapps
                '''
            }
        }
    }
}
