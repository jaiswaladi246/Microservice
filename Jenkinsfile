pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'K8-7', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://4A982777777CB35B3C2D38555A2942A7.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
            }
        }
    }
    
    stage('Verify Deployment To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'K8-7', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://4A982777777CB35B3C2D38555A2942A7.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc "
            }
        }
    }
}
}
