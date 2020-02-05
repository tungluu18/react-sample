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
        stage {
            image.inside("-e MODE=production") {
                sh "echo testing... $MODE"
            }
        }
    }
}
