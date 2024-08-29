pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MyDemoCluster', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://ACB86E909D5B22361CF3691969A2C7A0.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh 'kubectl apply -f deployment-service.yaml'
                    sleep 60
                }
            }
        }
        
        stage('Verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MyDemoCluster', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://ACB86E909D5B22361CF3691969A2C7A0.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh 'kubectl get all -n webapps'
                }
            }
        }
    }
}
