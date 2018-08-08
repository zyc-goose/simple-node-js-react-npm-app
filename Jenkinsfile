pipeline {
    agent any
    environment { 
        CI = 'true'
    }
    stages {
        stage('Sheep') {
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
