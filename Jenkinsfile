pipeline {
    agent {
        node {
            label 'maven'
        }
    }
environment {
    PATH = "/opt/maven/latest/bin:$PATH"
}
    stages {
        stage('build'){
            steps{
                sh 'mvn clean deploy'
            }

        }
        stage('SonarQube Analysis'){
        environment {
            scannerHome = tool 'SonarScanner'
        }
            steps{
                withSonarQubeEnv('sonarqube-server'){
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }

        }
    }
}
