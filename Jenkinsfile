pipeline {
    agent { node { label 'frontend' } }

    stages {
        stage('Build') {
            steps {
                sh "docker build -t frontend_image ."
            }
        }
        /*stage('Test') {
            steps {
                echo "Testing"
            }
        }*/
        stage('Deploy') {
            steps {
                sh "docker container rm frontend"
                sh "docker run -d --name frontend frontend_image"
            }
        }
    }
}