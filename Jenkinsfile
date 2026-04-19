pipeline {
    agent any

    environment {
        PATH = "/home/azad/.nvm/versions/node/v24.11.0/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Debug') {
            steps {
                sh '''
                    echo "PATH=$PATH"
                    which node
                    node -v
                    which npm
                    npm -v
                '''
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh '''
                    export PATH=/home/azad/.nvm/versions/node/v24.11.0/bin:$PATH
                    which node
                    node -v
                    which npm
                    npm -v
                    ./jenkins/scripts/test.sh
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}
