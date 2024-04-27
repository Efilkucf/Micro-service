pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'rrr-1', contextName: '', credentialsId: 'kubeconfig-jenkins-id', namespace: 'webapps', serverUrl: 'https://C9A15F6A2860D551CB0F2DBE3E19FEDE.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                }
            }
        }
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'rrr-1', contextName: '', credentialsId: 'kubeconfig-jenkins-id', namespace: 'webapps', serverUrl: 'https://C9A15F6A2860D551CB0F2DBE3E19FEDE.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
