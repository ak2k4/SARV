pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'SARV-EKS', contextName: '', credentialsId: 'k8-tokens', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://E18149ED95DDE6459E9D008DF01EE466.gr7.ap-south-1.eks.amazonaws.com') {
                    sh "kubectl apply -f deployment-service.yml"
                    
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
               withKubeConfig(caCertificate: '', clusterName: 'SARV-EKS', contextName: '', credentialsId: 'k8-tokens', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://E18149ED95DDE6459E9D008DF01EE466.gr7.ap-south-1.eks.amazonaws.com') {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
