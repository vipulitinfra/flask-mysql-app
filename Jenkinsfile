pipeline {

    agent any

    stages {

        stage('Clone Repository') {

            steps {

                git 'https://github.com/vipulitinfra/flask-mysql-app.git'

            }

        }

        stage('Build Containers') {

            steps {

                sh 'docker-compose build'

            }

        }

        stage('Deploy') {

            steps {

                sh '''
                docker-compose down || true
                docker-compose up -d
                '''
            }

        }

    }

}
