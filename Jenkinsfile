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
      
	
	}
	}
