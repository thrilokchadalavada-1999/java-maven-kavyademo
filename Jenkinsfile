pipeline {
    agent any

    tools {
        jdk 'Kavya JDK'
        maven 'kavyamaven3'
    }

    environment {
        DOCKER_HUB = 'kavya1111999'
        IMAGE_NAME = 'my-java-app'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/thrilokchadalavada-1999/java-maven-kavyademo.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t %DOCKER_HUB%/%IMAGE_NAME% .'
            }
        }

        stage('Docker Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-kavyacreds', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    bat 'echo %PASS% | docker login -u %USER% --password-stdin'
                    bat 'docker push %DOCKER_HUB%/%IMAGE_NAME%'
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f deploy.yaml'
                bat 'kubectl apply -f service.yaml'
                bat 'kubectl apply -f kavyaingress.yaml'
            }
        }
    }
}
