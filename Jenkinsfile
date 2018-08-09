pipeline {
    agent none
    environment { 
        CI = 'true'
    }
    stages {
        stage('Sheep') {
            agent {
                docker {
                    image 'node:10-alpine'
                    args '-p 3000:3000'
                }
            }
            steps {
		        sh 'npm --version'
		        sh 'node --version'
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('Chimpanzee') { 
            agent {
                docker {
                    image 'nginx'
                    args '-p 3000:80'
                }
            }
            steps {
                input message: 'Finished using the web site? (Click "Proceed" to continue)' 
            }
        }
    }
}
