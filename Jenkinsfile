pipeline {
    agent any

     parameters {
        string(name: 'BRANCH_NAME', defaultValue: '', description: 'Git branch to clone')

     }
    stages {

      stage('Clone the repository') {
            steps {
                git branch: "${params.BRANCH_NAME}", credentialsId: 'github-cred', url: 'https://github.com/techworldwithmurali/ingress.git'
            }
        }
         stage('Connect to the EKS Cluster') {
            steps {
                script {
                    // Ensure AWS CLI is configured with the right credentials before this step
                    sh '''
                    aws eks update-kubeconfig --name dev-cluster --region us-east-1
                    kubectl get nodes
                    '''
                }
            }
        }
    }
}
