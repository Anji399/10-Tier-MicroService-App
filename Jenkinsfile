pipeline {
    agent any
    environment {
      AWS_ACCESS_KEY_ID = 'AWS_ACCESS_KEY_ID'
      AWS_SECRET_ACCESS_KEY = 'AWS_SECRET_ACCESS_KEY'
    }
    stages {
        stage('K8-Deploy') {
    steps {
        withCredentials([aws(credentialsId: 'aws-credentials-id')]) {
            script {
                sh 'aws eks --region ap-south-1 update-kubeconfig --name my-eks2'
                sh 'kubectl apply -f deployment-service.yml'
                sh 'kubectl get pods -n webapps'
            }
        }
    }
}

