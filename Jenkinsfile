pipeline {
    agent any

    stages {
        stage('K8-Deploy') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: '', contextName: '', credentialsId: 'k8s', namespace: '', restrictKubeConfigAccess: false, serverUrl: '') {
                            sh 'kubectl apply -f deployment-service.yml'
                            sh 'kubectl get pods -n webapps'
                            sh 'kubectl get svc -n webapps'
                }
            }           
        }
    }
}
