pipeline {
    agent any

    stages {
        stage('K8-Deploy') {
          steps {
            withKubeConfig(
                caCertificate: '', 
                clusterName: 'my-eks2', 
                contextName: '', 
                credentialsId: 'k8-token', 
                namespace: 'webapps', 
                restrictKubeConfigAccess: false, 
                serverUrl: ''
            ) {
                script {
                    try {
                        sh 'kubectl apply -f deployment-service.yml'
                        sh 'kubectl get pods -n webapps'
                        sh 'kubectl get svc -n webapps'
                    } catch (Exception e) {
                        error "Kubernetes deployment failed: ${e.message}"
                    }
                }
            }
        }
    }
}

