stage('Docker Push') {
    steps {
        withCredentials([usernamePassword(
            credentialsId: 'docker-kavya1creds',
            usernameVariable: 'DOCKER_USER',
            passwordVariable: 'DOCKER_PASS'
        )]) {
            bat '''
            docker login -u %DOCKER_USER% -p %DOCKER_PASS%
            docker push kavya1111999/my-java-app
            '''
        }
    }
}
