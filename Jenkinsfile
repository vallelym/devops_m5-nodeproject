pipeline {
    agent any

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
                export PATH=$PWD/node-v18.0.0-linux-x64/bin:$PATH

                # Verify installation
                node -v
                npm -v
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
