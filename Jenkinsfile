pipeline {
    agent { label 'jenkins-Salve'}
    tools {
        jdk 'java17'
        maven 'maven3'
    }

    environment {
        APP_NAME = "register-app-pipeline"
        RELEASE = "1.0.0"
    }

    stages {
        stage ("Clean workspace") {
            steps {
                cleanWs()
            }
        }

        stage ("Checkout from github repo") {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'Zee-Github-creden', url: 'https://github.com/Zeeshanmedlari/register-app.git']])
            }
        }

        stage ("Build the Application") {
            steps {
                sh "mvn clean package"
            }
        }
        
        stage ("Test Application") {
            steps {
                sh "mvn test"
            }
        }
    }

}
