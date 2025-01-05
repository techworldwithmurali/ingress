  pipeline {
    agent any
    parameters {
        string(name: 'BRANCH', defaultValue: 'deploy-to-eks-dockerhub-jenkinsfile', description: 'Git branch to clone')

    }

  environment {
        AWS_REGION = 'us-east-1'
        EKS_CLUSTER = 'dev-cluster'

  }
	  
    stages {

stage('Clone') {
            steps {
                git branch: "${params.BRANCH}", credentialsId: 'github-cred', url: 'https://github.com/techworldwithmurali/ingress.git'
            }
        }

	    stage('Set Up AWS EKS Config') {
            steps {
                script {
                    sh """
                    aws eks update-kubeconfig --name ${EKS_CLUSTER} --region ${AWS_REGION}
                    """
                }
            }
        }

      
        
        }
		
  }
