pipeline {
    agent any
    
    stages {
        stage('Budowa obrazu Backend') {
            steps {
                dir('backend') {
                    echo 'Budowanie obrazu dla backendu (Node.js)...'
                    sh 'docker build -t trello-clone-backend:latest .'
                }
            }
        }
        stage('Budowa obrazu Frontend') {
            steps {
                dir('frontend') {
                    echo 'Budowanie obrazu dla frontendu (Nginx)...'
                    sh 'docker build -t trello-clone-frontend:latest .'
                }
            }
        }
    }
}