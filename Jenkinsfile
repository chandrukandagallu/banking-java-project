pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                // Checkout code from GitHub
                git branch: 'main', url: 'https://github.com/chandrukandagallu/banking-java-project.git'
            }
        }

        stage('Build') {
            steps {
                // Make mvnw executable and build the project
                sh 'chmod +x mvnw'
                sh './mvnw clean package'
            }
        }

        stage('Docker Build & Run') {
            steps {
                // Build Docker image and run container on port 8090
                sh 'docker build -t banking-app .'
                sh 'docker run -d -p 8090:8080 banking-app'
            }
        }

        stage('Expose Port') {
            steps {
                echo 'Application is running on port 8090'
            }
        }
    }
}
