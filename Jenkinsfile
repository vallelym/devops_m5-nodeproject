pipeline {
    agent any

    environment {
        NODE_HOME = "${env.WORKSPACE}/node-v18.0.0-linux-x64"
        PATH = "${NODE_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/vallelym/devops_m5-nodeproject.git', branch: 'main'
            }
        }
        stage('Install NodeJS and npm') {
            steps {
                sh '''
                # Download NodeJS binaries
                curl -o node-v18.0.0-linux-x64.tar.xz https://nodejs.org/dist/v18.0.0/node-v18.0.0-linux-x64.tar.xz
                tar -xf node-v18.0.0-linux-x64.tar.xz

                # Verify installation
                ${NODE_HOME}/bin/node -v
                ${NODE_HOME}/bin/npm -v
                '''
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Run Application') {
            steps {
                sh 'nohup node index.js &'
            }
        }
    }
}
