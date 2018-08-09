pipeline {
    agent {
        docker {
            image 'ubuntu:xenial'
        }
    }
    environment { 
        CI = 'true'
    }
    stages {
        stage('Sheep') {
            steps {
		        sh 'sudo apt update'
		        sh 'sudo apt install node'
                sh 'node --version'
                sh 'npm --version'
            }
        }
        stage('Chimpanzee') { 
            steps {
                input message: 'Finished using the web site? (Click "Proceed" to continue)' 
            }
        }
    }
}
