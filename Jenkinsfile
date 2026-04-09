pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        
        stage('build'){
            steps{
                sh 'mvn clean package'
            }
        }

        stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'sonar-scanner'
            }

            steps {
                withSonarQubeEnv('sonar-siva') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }




    }
}
