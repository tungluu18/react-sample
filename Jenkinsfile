pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                scripts {
                    def image = docker.build("node")
                    image.inside("-e MODE=development") {
                        sh "echo testing... $MODE"
                    }
                }
            }
        }
    }
}
