pipeline {
    agent any
    
    stages {
        stage('Pobranie i weryfikacja kodu') {
            steps {
                echo 'Sprawdzanie struktury katalogów pobranej z GitHuba...'
                sh 'ls -la'
                sh 'ls -la backend/'
                sh 'ls -la frontend/'
            }
        }
        stage('Przygotowanie do budowy') {
            steps {
                dir('backend') {
                    echo 'Katalog backendu wykryty. Gotowość do wykonania docker build...'
                }
                dir('frontend') {
                    echo 'Katalog frontendu wykryty. Gotowość do wykonania docker build...'
                }
            }
        }
    }
}