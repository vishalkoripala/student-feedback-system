pipeline {
    agent any
    environment {
        IMAGE_NAME = 'student-feedback-app'
        CONTAINER_NAME = 'student-feedback-app'
        DOCKER_PORT = '5000'
    }
    stages {
        stage('Checkout Code') {
            steps {
                // Replace with your GitHub repo URL
                git 'https://github.com/your-username/student-feedback-system.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    bat "docker build -t %IMAGE_NAME% ."
                }
            }
        }
        stage('Stop and Remove Old Container') {
            steps {
                script {
                    // Stop and remove if running
                    bat "docker stop %CONTAINER_NAME% || exit 0"
                    bat "docker rm %CONTAINER_NAME% || exit 0"
                }
            }
        }
        stage('Run New Container') {
            steps {
                script {
                    bat "docker run -d --name %CONTAINER_NAME% -p %DOCKER_PORT%:5000 %IMAGE_NAME%"
                }
            }
        }
    }
}
