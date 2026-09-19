pipeline {
    agent any

    environment {
        PATH = "/opt/maven/bin:${env.PATH}"
        SCANNER_HOME = tool 'sonar-card'
    }

    stages {

        stage('Maven Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonar-card-1') {
                    sh "${SCANNER_HOME}/bin/sonar-scanner"
                }
            }
        }
    }
}

