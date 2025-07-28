pipeline {
    agent any

    environment {
        IMAGE_NAME = 'priacc-flask-app'
        CONTAINER_NAME = 'priacc-container'
    }

    stages {
        stage('Git Clone') {
            steps {
                git url: 'https://github.com/Uday-rajanala/python.git',
                    branch: 'main',
                    credentialsId: 'github-token'
            }
        }

        stage('List Files') {
            steps {
                sh 'ls -la'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t $IMAGE_NAME ."
            }
        }

        stage('Run App in Docker') {
            steps {
                sh "docker rm -f $CONTAINER_NAME || true"
                sh "docker run -d --name $CONTAINER_NAME -p 5000:5000 $IMAGE_NAME"
            }
        }
    }

    post {
        always {
            echo 'Cleaning workspace...'
            deleteDir()
        }
    }
}

