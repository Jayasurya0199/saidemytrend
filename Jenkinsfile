pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    
    stages {
        stage('GitHub Clone') {
            steps {
                git url: 'https://github.com/Jayasurya0199/saidemytrend.git', branch: 'main'
            }
        }
        stage("build") {
            steps {
                sh 'mvn clean deploy'
            }
        }
        stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'sonarqube-scanner'
            }
            steps {
                withSonarQubeEnv('sonarqube-server') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
        

    }
}
