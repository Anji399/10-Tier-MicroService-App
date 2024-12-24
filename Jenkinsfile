pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'my-eks2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: '']]) {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'my-eks2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: '']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}

