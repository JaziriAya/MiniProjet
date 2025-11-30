pipeline {
    agent any

    tools {
        // Utilisez le NOM EXACT configuré dans Jenkins
        maven 'maven'                    // ou le nom exact que vous voyez
        jdk 'jdk17'                      // ou le nom exact que vous voyez
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
