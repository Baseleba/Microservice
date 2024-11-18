pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://529274788E181010BFCF05A7D9623829.gr7.us-east-1.eks.amazonaws.com') {
                    sh "kubectl apply -f deployment-service.yml"
                
                }
            }
        }
        stage('Verify Deployment') { 
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://529274788E181010BFCF05A7D9623829.gr7.us-east-1.eks.amazonaws.com') {
                    sh "kubectl get svc -n webapps"
                }
                    
            }
        }
    }
}
