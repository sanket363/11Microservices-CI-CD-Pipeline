pipeline {
    agent any

    environment {
        K8S_CLUSTER_NAME = 'EKS-1'
        K8S_NAMESPACE = 'webapps'
        K8S_SERVER_URL = 'server-url'
        K8S_CREDENTIALS_ID = 'k8-token' // create a secret with this name
    }

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: "${env.K8S_CLUSTER_NAME}", contextName: '', credentialsId: "${env.K8S_CREDENTIALS_ID}", namespace: "${env.K8S_NAMESPACE}", serverUrl: "${env.K8S_SERVER_URL}"]]) {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: "${env.K8S_CLUSTER_NAME}", contextName: '', credentialsId: "${env.K8S_CREDENTIALS_ID}", namespace: "${env.K8S_NAMESPACE}", serverUrl: "${env.K8S_SERVER_URL}"]]) {
                    sh "kubectl get svc -n ${env.K8S_NAMESPACE}"
                }
            }
        }
    }
}
