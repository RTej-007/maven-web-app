pipeline {
    agent any
    tools{
        maven 'maven-3.6.3'
    }

    stages {
        stage('GIT Clone') {
            steps {
            git credentialsId: 'Github_username_password', url: 'https://github.com/RTej-007/maven-web-app.git'
            }
        }

        stage('MAVEN Build') {
            steps {
            sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
            deploy adapters: [tomcat9(credentialsId: 'Tomcat-credntials', path: '', url: 'http://65.0.176.12:8080/')], contextPath: 'maven-web-app', war: '**/*.war'
                 }
        }
    }
}
