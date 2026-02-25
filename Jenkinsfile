pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks-cluster-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://16A22378491B5502C07653804592395B.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks-cluster-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://16A22378491B5502C07653804592395B.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
