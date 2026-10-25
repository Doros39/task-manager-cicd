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
                
                // Zatrzymanie i usunięcie starych kontenerów
                sh 'docker stop trello-backend || true'
                sh 'docker rm trello-backend || true'
                sh 'docker stop trello-frontend || true'
                sh 'docker rm trello-frontend || true'
                
                // Uruchomienie najnowszych wersji
                sh 'docker run -d --name trello-backend -p 5000:5000 trello-clone-backend:latest'
                sh 'docker run -d --name trello-frontend -p 3000:80 trello-clone-frontend:latest'
            }
        }
    }
}