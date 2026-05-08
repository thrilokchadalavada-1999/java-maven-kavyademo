pipeline {

    agent any

    environment {
        DOCKER_IMAGE = "kavya1111999/my-java-app:v8"
        CONTAINER_NAME = "my-java-app"
    }

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/thrilokchadalavada-1999/java-maven-kavyademo.git'
            }
        }

        stage('Build Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Push Docker Image') {
            steps {

                withCredentials([usernamePassword(
                    credentialsId: 'kavyadockerhub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {

                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'

                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }

        stage('Deploy Container') {
            steps {

                sh '''
                docker stop $CONTAINER_NAME || true
                docker rm $CONTAINER_NAME || true

                docker pull $DOCKER_IMAGE

                docker run -d \
                  --name $CONTAINER_NAME \
                  --restart unless-stopped \
                  -p 80:8080 \
                  $DOCKER_IMAGE
                '''
            }
        }
    }
}
