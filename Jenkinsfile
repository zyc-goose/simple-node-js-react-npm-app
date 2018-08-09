pipeline {
    agent {
        docker {
            image 'node:10-alpine'
            args '-p 3000:3000'
        }
    }
    environment { 
        CI = 'true'
    }
    stages {
        stage('Sheep') {
            steps {
		        sh 'npm --version'
		        sh 'node --version'
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('Goat') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Chimpanzee') { 
            agent {
                dockerfile true
            }
            steps {
                sh './jenkins/scripts/deliver.sh' 
                input message: 'Finished using the web site? (Click "Proceed" to continue)' 
                sh './jenkins/scripts/kill.sh' 
            }
        }
    }
}
