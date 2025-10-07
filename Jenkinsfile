pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                // Only one git checkout
                git branch: 'main', url: 'https://github.com/chandrukandagallu/banking-java-project.git'
            }
        }

        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
        }

        stage('Docker Build & Run') {
            steps {
                sh 'docker build -t banking-app .'
                sh 'docker run -d -p 8080:8080 banking-app'
            }
        }

        stage('Expose Port') {
            steps {
                echo 'Application is running on port 8080'
            }
        }
    }
}
