pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: 'webapps', credentialsId: 'k8-token', namespace: '', serverUrl: 'https://8756FE7FF9D1A054741430FC131767C0.gr7.ap-south-1.eks.amazonaws.com']]) {
                 sh 'kubectl apply -f deployment-service.yml'
                 sleep 60
                }
            }
        }
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: 'webapps', credentialsId: 'k8-token', namespace: '', serverUrl: 'https://8756FE7FF9D1A054741430FC131767C0.gr7.ap-south-1.eks.amazonaws.com']]) {
                 sh 'kubectl get all -n webapps'
                }
                
            }
        }
    }
}
