pipeline {
    agent any

    tools {
        maven 'Apache Maven 3.8.7' // Ensure this name matches Jenkins Maven configuration
    }

    stages {
        stage('Checkout the Code from GitHub') {
            steps {
                git url: 'https://github.com/Pradeep-kumar11/banking_finance'
                echo 'GitHub repository checked out'
            }
        }

        stage('Code Compile with pradeep') {
            steps {
                echo 'Starting code compilation'
                sh 'mvn compile'
            }
        }

        stage('Code Testing with pradeep') {
            steps {
                echo 'Running unit tests'
                sh 'mvn test'
            }
        }

        stage('QA with pradeep') {
            steps {
                echo 'Running code quality checks'
                sh 'mvn checkstyle:checkstyle'
            }
        }

        stage('Package with pradeep') {
            steps {
                echo 'Packaging application'
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image'
                sh 'docker build -t pradeep781/bankingproject:latest .'
            }
        }

        stage('Docker Login Credentials') {
            steps {
        echo 'Logging into DockerHub'
        withCredentials([string(credentialsId: 'dockerhubpassword', variable: 'dockerhubpass')]) {
            sh "docker login -u ${dockerhubusername} -p ${dockerhubuserpw}"
                }
            }
        }

        stage('Image Push to DockerHub') {
            steps {
                echo 'Pushing Docker image to DockerHub'
                sh 'docker push pradeep781/bankingproject:latest'
            }
        }

        stage('Deploy Application using Ansible') {
            steps {
                echo 'Deploying application using Ansible playbook'
                ansiblePlaybook credentialsId: 'private-key', disableHostKeyChecking: true, installation: 'Ansible2', inventory: '/etc/ansible/hosts', playbook: 'ansible-playbook.yml', vaultTmpPath: ''
            }
        }
    }
}
