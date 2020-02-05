pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }
    stages {
        def image = docker.build("node")
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                image.inside("-e MODE=development") {
                    sh "echo testing... $MODE"
                }
            }
        }
    }
}
