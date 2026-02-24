pipeline {
    agent any

    tools {
    maven 'Maven-3.9.12'
    jdk 'jdk-21'
}


    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'master', url: 'https://github.com/ArnavRade/DevOps_5023142.git'
                 
            }
        }

        stage('Build with Maven') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: 'tomcat-creds',
                        path: '',
                        url: 'http://localhost:8081'
                    )
                ],
                contextPath: 'my-web-app',
                war: 'target/*my-webapp.war'
            }
        }
    }
}
