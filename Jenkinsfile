pipeline {
    agent {
        node {
            label 'maven'
        }
    }

    environment {
        PATH = "/opt/maven/latest/bin:$PATH"
        scannerHome = tool 'SonarScanner'
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean deploy'
            }
        }

        stage('SonarCloud Analysis') {
            steps {
                withCredentials([string(credentialsId: 'sonar-Cred', variable: 'SONAR_TOKEN')]) {
                    sh "${scannerHome}/bin/sonar-scanner -Dsonar.login=$SONAR_TOKEN"
                }
            }
        }
    }
}
