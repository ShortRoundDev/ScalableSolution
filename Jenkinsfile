def build_image(){
    sh "rm -rf ___scalableSolution"
    sh "git clone https://github.com/shortrounddev/scalableSolution/ ___scalableSolution"
    dir("___scalableSolution"){
        sh "docker build -t frontend_image ."
    }
    sh "rm -rf ___scalableSolution"
}

def deploy_container(){
    sh "(docker stop frontend && docker container rm frontend) || true"
    sh "docker run -d --name frontend -p 80:80 -p 443:443 frontend_image"
}

def run_on_all(Closure func){
    node('fe1'){
        func()
    }
    node('fe2'){
        func()
    }
    node('fe3'){
        func()
    }
}

pipeline {
    agent none

    stages {
        stage('Build') {
            steps {
               run_on_all(this.&build_image)
            }
        }
        /*stage('Test') {
            steps {
                echo "Testing"
            }
        }*/
        stage('Deploy') {
            steps {
               run_on_all(this.&deploy_container)
            }
        }
    }
}

