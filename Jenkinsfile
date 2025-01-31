pipeline {
    agent any

    environment {
        DOCKER_CREDENTIALS_ID = 'your-docker-credentials-id'
        DOCKER_IMAGE = 'registry.gitlab.com/your-username/your-repo:latest'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/vallelym/devops_m5-nodeproject.git', branch: 'main'
            }
        }
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
                    docker.withRegistry('https://registry.gitlab.com', DOCKER_CREDENTIALS_ID) {
                        docker.image('my-node-app').push('latest')
                    }
                }
            }
        }
    }
}
