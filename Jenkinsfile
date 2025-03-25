pipeline {

    agent any

    stages {

        stage('checkout the code from github') {

            steps {

                git url: 'https://github.com/Pradeep-kumar11/banking_finance'

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

 
