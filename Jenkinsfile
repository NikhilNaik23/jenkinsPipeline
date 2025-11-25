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
                sh 'docker rm -f html-container || true'
                sh 'docker run -d -p 8080:80 --name html-container my-html-website'
            }
        }
    }
}
