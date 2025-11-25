pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/YourUsername/your-html-repo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("my-html-website")
                }
            }
        }

        stage('Deploy Container') {
            steps {
                script {
                    // Stop old container if running
                    sh 'docker rm -f html-container || true'
                    // Run new container
                    sh 'docker run -d -p 8080:80 --name html-container my-html-website'
                }
            }
        }
    }
}
