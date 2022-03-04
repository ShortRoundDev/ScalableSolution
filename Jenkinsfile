pipeline {
    agent {
        node('fe1')
        node('fe2')
        node('fe3')
    }

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
                sh "docker stop frontend"
                sh "docker container rm frontend"
                sh "docker run -d --name frontend frontend_image"
            }
        }
    }
}