pipeline {
    agent any
  
    stages {

      stage('Clone the repository') {
            steps {
                git branch: 'helm-deploy-on-eks-dockerhub-jenkinsfile', credentialsId: 'github-cred', url: 'https://github.com/techworldwithmurali/ingress.git'
            }
        }
    }
}
