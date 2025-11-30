pipeline {
    agent any

    tools {
        maven 'maven.4.0'
        jdk 'openjdk version 17'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/JaziriAya/MiniProjet.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [tomcat9('Tomcat9')], 
                contextPath: 'monapp',
                war: 'target/*.war'
            }
        }
    }
}
