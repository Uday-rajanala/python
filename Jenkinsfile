pipeline {
    agent any

    environment {
        IMAGE = 'uday'
        VERSION = "${BUILD_NUMBER}"
    }

    stages {
        stage('Clone Repo') {
            steps {
                echo "Cloning the repository"
                sh 'pwd'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t $IMAGE:$VERSION .'
            }
        }

        stage('Build Container') {
            steps {
                sh 'docker run --name container1 -dp 5000:5000 $IMAGE:$VERSION'
            }
        }
    }
}
