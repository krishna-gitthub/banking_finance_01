pipeline {

    agent any
 
    environment {

        IMAGE_NAME = 'rojabonakurthi96/myproject'

        IMAGE_TAG = '1.0'

    }
 
    stages {

        stage('Checkout the Code from GitHub') {

            steps {

                git url: 'https://github.com/rojabonakurthi96/Banking-java-project/'

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

                        echo "$DOCKER_HUB_PASS" | docker login -u rojabonakurthi96 --password-stdin

                        docker push ${IMAGE_NAME}:${IMAGE_TAG}

                    """

                }

            }

        }

    }

}
 
Atul Swain added Roja Bonakurthi to the chat and shared all chat history.

 
pipeline {.txt
 
git ls-remote https://github.com/Pradeep-kumar11/banking_finance.git

GitHub - Pradeep-kumar11/banking_finance
Contribute to Pradeep-kumar11/banking_finance development by creating an account on GitHub.
 
pipeline {

    agent any

    stages {

        stage('checkout the code from github') {

            steps {

                git url: 'https://github.com/sumitsingh231/Banking-java-project/'

                echo 'GitHub URL checked out'

            }

        }

        stage('codecompile with sumit') {

            steps {

                echo 'Starting compilation'

                sh 'mvn compile'

            }

        }

        stage('codetesting with sumit') {

            steps {

                sh 'mvn test'

            }

        }

        stage('qa with sumit') {

            steps {

                sh 'mvn checkstyle:checkstyle'

            }

        }

        stage('package with sumit') {

            steps {

                sh 'mvn package'

            }

        }

        stage('run dockerfile') {

            steps {

                sh 'docker build -t myimg .'

            }

        }

        stage('run container') {

            steps {

                sh 'docker run -d -p 8092:8091 --name myapp myimg'

                echo 'Container is running on port 8092'

            }

        }

    }

}

 
