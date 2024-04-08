pipeline { 
    agent any 

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'K8-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://0D208B3EF213BF0BC4450AA2413A0151.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 10
            }
        }
    }
    
    stage('Verify Deployment To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'K8-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://0D208B3EF213BF0BC4450AA2413A0151.gr7.ap-south-1.eks.amazonaws.com']]) {
    
                    sh "kubectl get svc "
            }
        }
    }
}
}
