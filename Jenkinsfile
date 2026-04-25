pipeline {
    agent any

    tools {
        jdk 'KavyaJDK17'
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
               withCredentials([usernamePassword(credentialsId: 'docker-kavyacreds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
    bat """
    echo %DOCKER_PASS% | docker login -u %DOCKER_USER% --password-stdin
    docker push kavya1111999/my-java-app
    """
}
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
