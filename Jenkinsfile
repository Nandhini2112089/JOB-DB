pipeline {
    agent any

    environment {
        DOCKERHUB_USER = 'sivanandhini23'
        IMAGE_NAME = "${DOCKERHUB_USER}/job-portal"
    }

    stages {
        stage('Check Docker Access') {
            steps {
                sh 'docker --version'
                sh 'docker ps'
            }
        }

        stage('Unzip Binary') {
            steps {
                sh 'unzip -o dist/my_app.zip -d dist/'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -f Dockerfile-goapp -t $IMAGE_NAME .'
            }
        }

        stage('Docker Hub Login') {
            steps {
			sh 'docker login -u $DOCKERHUB_USER -p Nandhini@23'
               
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push $IMAGE_NAME'
            }
        }
    }
}
