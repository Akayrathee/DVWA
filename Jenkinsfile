pipeline {
    agent any 
    
    stages { 
        stage('SCM Checkout') {
            steps{
           git branch: 'master', url: 'https://github.com/Akayrathee/DVWA'
            }
        }
        // run sonarqube test
        stage('Run Sonarqube') {
            environment {
                scannerHome = tool 'sonarqube-scanner';
            }
            steps {
              withSonarQubeEnv(credentialsId: 'sonarqube_token', installationName: 'Sonarqube') {
                sh "${scannerHome}/bin/sonar-scanner"
              }
            }
        }
    }
}
