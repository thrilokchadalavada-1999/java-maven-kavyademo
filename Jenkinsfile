pipeline {
agent any

```
tools {
    jdk 'KavyaJDK17'
    maven 'kavyamaven3'
}

environment {
    DOCKER_IMAGE = 'kavya1111999/my-java-app'
    KUBECONFIG = '/var/lib/jenkins/.kube/config'
}

stages {

    stage('Checkout') {
        steps {
            git branch: 'main', url: 'https://github.com/thrilokchadalavada-1999/java-maven-kavyademo.git'
        }
    }

    stage('Build') {
        steps {
            sh 'mvn clean package'
        }
    }

    stage('Docker Build') {
        steps {
            sh 'docker build -t $DOCKER_IMAGE .'
        }
    }

    stage('Docker Push') {
        steps {
            withCredentials([usernamePassword(
                credentialsId: 'docker-credentials',
                usernameVariable: 'DOCKER_USER',
                passwordVariable: 'DOCKER_PASS'
            )]) {
                sh '''
                echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin
                docker push $DOCKER_IMAGE
                '''
            }
        }
    }

    stage('Deploy to Kubernetes') {
        steps {
            sh '''
            kubectl get nodes
            kubectl apply -f deploy.yaml
            kubectl apply -f service.yaml
            '''
        }
    }
}
```

}
