pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 4000:4000'
        }
    }
    environment { 
        CI = 'true'
    }
    stages {
        stage('Sheep') {
            agent {
                docker {
                    image: 'node:10-alpine'
                    args: '-p 3000:3000'
                }
            }
            steps {
		sh 'npm --version'
		sh 'node --version'
                sh 'npm install'
            }
        }
        stage('Goat') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Chimpanzee') { 
            steps {
                sh './jenkins/scripts/deliver.sh' 
                input message: 'Finished using the web site? (Click "Proceed" to continue)' 
                sh './jenkins/scripts/kill.sh' 
            }
        }
    }
}
