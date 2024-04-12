pipeline { 
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: '', namespace: 'webapps', serverUrl: 'https://9947C5066B210310095832ADB53E5DE3.gr7.ap-south-1.eks.amazonaws.com']]) 
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: '', namespace: 'webapps', serverUrl: 'https://9947C5066B210310095832ADB53E5DE3.gr7.ap-south-1.eks.amazonaws.com']])
                    sh "kubectl get all -n webapps"
                }
            }
}
