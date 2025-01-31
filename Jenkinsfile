pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    docker.build('my-node-app')
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    docker.withRegistry('https://registry.gitlab.com', 'gitlab-credentials-id') {
                        docker.image('my-node-app').push('latest')
                    }
                }
            }
        }
    }
}
