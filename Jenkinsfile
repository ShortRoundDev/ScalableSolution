pipeline {
    agent { node { label 'frontend' } }

    stages {
        stage('Build') {
            steps {
                sh 'ls'
            }
        }
        stage('Test') {
            steps {
                echo "Testing"
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying"
            }
        }
    }
}