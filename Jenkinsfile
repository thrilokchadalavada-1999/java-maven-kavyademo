
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
    }
}
