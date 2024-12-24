pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeConfig(
                    caCertificate: '', 
                    clusterName: 'my-eks2', 
                    contextName: '', 
                    credentialsId: 'k8-token', 
                    namespace: 'webapps', 
                    restrictKubeConfigAccess: false, 
                    serverUrl: 'https://2B6C84D4E43226B27E20E49AA6680F53.gr7.ap-south-1.eks.amazonaws.com'
                ) {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeConfig(
                    caCertificate: '', 
                    clusterName: 'my-eks2', 
                    contextName: '', 
                    credentialsId: 'k8-token', 
                    namespace: 'webapps', 
                    restrictKubeConfigAccess: false, 
                    serverUrl: 'https://2B6C84D4E43226B27E20E49AA6680F53.gr7.ap-south-1.eks.amazonaws.com'
                ) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}

