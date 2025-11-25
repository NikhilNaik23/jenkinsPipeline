pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/NikhilNaik23/jenkinsPipeline.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t my-html-website .'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying container...'
                sh 'docker stop html-container || true'
                sh 'docker rm html-container || true'
                sh 'docker run -d -p 8081:80 --name html-container my-html-website'
            }
        }
    }
}
