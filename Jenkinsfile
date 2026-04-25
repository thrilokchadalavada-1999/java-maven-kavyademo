pipeline {
    agent any

    environment {
        // Docker Hub repo details
        DOCKER_IMAGE = "kavya1111999/my-java-app:latest"
        // Path to kubeconfig file (adjust if Jenkins runs under a different account)
        KUBECONFIG = "C:\\Users\\thril\\.kube\\config"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/thrilokchadalavada-1999/java-maven-kavyademo.git'
            }
        }

        stage('Build with Maven') {
            steps {
                bat "mvn clean package"
            }
        }

        stage('Docker Build') {
            steps {
                bat "docker build -t ${DOCKER_IMAGE} ."
            }
        }

        stage('Docker Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-kavya1creds',
                                                 usernameVariable: 'DOCKER_USER',
                                                 passwordVariable: 'DOCKER_PASS')]) {
                    bat "echo %DOCKER_PASS% | docker login -u %DOCKER_USER% --password-stdin"
                    bat "docker push ${DOCKER_IMAGE}"
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                withEnv(["KUBECONFIG=${KUBECONFIG}"]) {
                    bat "kubectl apply -f deploy.yaml --validate=false"
                    bat "kubectl apply -f service.yaml --validate=false"
                }
            }
        }
    }
}
