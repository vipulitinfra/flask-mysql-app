pipeline {

    agent any

    environment {

        IMAGE_NAME = "vipulitinfra/flask-mysql-app"

    }

    stages {

        stage('Clone Repository') {

            steps {

                git url: 'https://github.com/vipulitinfra/flask-mysql-app.git',
                    branch: 'main'
                

            }

        }

        stage('Build Docker Image') {

            steps {

                sh '''
                docker build -t $IMAGE_NAME:latest .
                '''
            }

        }

        stage('Docker Login') {

            steps {

                withCredentials([
                usernamePassword(
                credentialsId: 'dockerhub-creds',
                usernameVariable: 'USER',
                passwordVariable: 'PASS'
                )
                ]) {

                sh '''
                echo $PASS | docker login -u $USER --password-stdin
                '''
                }
            }
        }

        stage('Push To Docker Hub') {

            steps {

                sh '''
                docker push $IMAGE_NAME:latest
                '''
            }

        }

    }

}
