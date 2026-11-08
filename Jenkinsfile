pipeline {
    agent any
    
    stages {
        stage('Budowa obrazu Backend') {
            steps {
                dir('backend') {
                    sh 'docker build -t trello-clone-backend:latest .'
                }
            }
        }
        stage('Budowa obrazu Frontend') {
            steps {
                dir('frontend') {
                    sh 'docker build -t trello-clone-frontend:latest .'
                }
            }
        }
        stage('Wdrozenie aplikacji (Deploy)') {
            steps {
                echo 'Uruchamianie nowych kontenerow...'
                
                sh 'docker stop trello-backend || true'
                sh 'docker rm trello-backend || true'
                sh 'docker stop trello-frontend || true'
                sh 'docker rm trello-frontend || true'
                
                sh 'docker run -d --name trello-backend -p 5000:5000 trello-clone-backend:latest'
                sh 'docker run -d --name trello-frontend -p 3000:80 trello-clone-frontend:latest'
            }
        }
    }
    post {
        success {
            slackSend(color: 'good', message: "✅ Wdrożenie udane! Projekt: ${env.JOB_NAME}, Budowa nr: #${env.BUILD_NUMBER}. Frontend działa na http://192.168.1.25:3000")
        }
        failure {
            slackSend(color: 'danger', message: "❌ Błąd wdrożenia! Projekt: ${env.JOB_NAME}, Budowa nr: #${env.BUILD_NUMBER}. Sprawdź logi w Jenkinsie.")
        }
    }
}