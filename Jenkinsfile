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
            scannaerhome = tool "sonarqube-scanner"
        }
            steps{
                withSonarQubeEnv("sonarqube-scanner"){
                    sh "${scannaerhome}/bin/sonar-scanner"
                }
            }

        }
    }
}
