pipeline {
    agent any

    environment {
        COMPOSE_FILE = "docker-compose.yml"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/nam712/deploy-jenkins.git'
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    sh 'docker compose pull || exit 1'  
                    sh 'docker compose down || exit 1' 
                    sh 'docker compose up -d || exit 1' 
                    sh 'docker image prune -af || true' 
                }
            }
        }
    }
}
