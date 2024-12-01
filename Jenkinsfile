pipeline {
    agent any

     parameters {
        string(name: 'BRANCH_NAME', defaultValue: 'helm-deploy-on-eks-dockerhub-jenkinsfile', description: 'Git branch to clone')
         string(name: 'RELEASE_NAME', defaultValue: '', description: 'RELEASE_NAME')
		string(name: 'namespace', defaultValue: '', description: 'namespace to deploy')

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

stage('Deploy the Application') {
            steps {
                script {
                    // Deploy the application with the provided parameters
                    sh '''
                    helm upgrade --install -f values-dev.yaml $RELEASE_NAME . -n $namespace
                    '''
                }
            }
        }
        
    }
}
