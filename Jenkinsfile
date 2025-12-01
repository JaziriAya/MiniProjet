pipeline {
    agent any

    stages {
        stage('Checkout Git') {
            steps {
                git branch: 'main', url: 'https://github.com/JaziriAya/MiniProjet.git'
            }
        }

        stage('Build Maven') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [tomcat9('Tomcat9')], 
                contextPath: 'miniprojet',
                war: 'target/*.war'
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline terminé - vérification des artefacts'
            sh 'ls -la target/*.war || true'
        }
        success {
            echo ' Build et déploiement réussis!'
        }
    }
}
