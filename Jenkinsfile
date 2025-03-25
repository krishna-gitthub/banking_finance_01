pipeline {

    agent any

    environment {
        IMAGE_NAME = 'pradeep-kumar11/myproject'
        IMAGE_TAG = '1.0'
    }

    stages {

        stage('Checkout the Code from GitHub') {
            steps {
                echo 'Checking out the GitHub repository...'
                git branch: 'main', url: 'https://github.com/Pradeep-kumar11/banking_finance'
            }
        }

        stage('Code Compilation') {
            steps {
                echo 'Starting compilation...'
                sh './mvnw compile'
            }
        }

        stage('Code Testing') {
            steps {
                echo 'Running tests...'
                sh './mvnw test'
            }
        }

        stage('QA Check (Checkstyle)') {
            steps {
                echo 'Running Checkstyle...'
                sh './mvnw checkstyle:checkstyle'
            }
        }

        stage('Package Application') {
            steps {
                echo 'Packaging application...'
                sh './mvnw package'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh """
                    if ! docker info > /dev/null 2>&1; then
                        echo "Docker is not running or accessible. Please start Docker."
                        exit 1
                    fi
                    docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .
                """
            }
        }

        stage('Login to Docker Hub and Push Image') {
            steps {
                withCredentials([string(credentialsId: 'dockerhubpassword', variable: 'DOCKER_HUB_PASS')]) {
                    sh """
                        echo "$DOCKER_HUB_PASS" | docker login -u pradeep781 --password-stdin
                        docker push ${IMAGE_NAME}:${IMAGE_TAG}
                    """
                }
            }
        }
    }
}
