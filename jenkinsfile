pipeline {

    agent any
 
    environment {

        IMAGE_NAME = 'pradeep-kumar11/myproject'

        IMAGE_TAG = '1.0'

    }
 
    stages {

        stage('Checkout the Code from GitHub') {

            steps {

                git url: 'https://github.com/Pradeep-kumar11/banking_finance'

                echo 'GitHub repository checked out'

            }

        }
 
        stage('Code Compilation') {

            steps {

                echo 'Starting compilation'

                sh 'mvn compile'

            }

        }
 
        stage('Code Testing') {

            steps {

                echo 'Running tests'

                sh 'mvn test'

            }

        }
 
        stage('QA Check (Checkstyle)') {

            steps {

                echo 'Running Checkstyle'

                sh 'mvn checkstyle:checkstyle'

            }

        }
 
        stage('Package Application') {

            steps {

                echo 'Packaging application'

                sh 'mvn package'

            }

        }
 
        stage('Build Docker Image') {

            steps {

                echo 'Building Docker image'

                sh "docker build -t ${IMAGE_NAME}:${IMAGE_TAG} ."

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
 
