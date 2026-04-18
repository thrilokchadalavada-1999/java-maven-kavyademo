pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {
        stage('Build') {
            steps {
                bat 'mvn -version'
            }
        }

        stage('Compile') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Check Target') {
            steps {
                bat 'dir target'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t my-java-app .'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p 8081:8080 my-java-app'
            }
        }
    }
}
