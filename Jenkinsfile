pipeline {

    agent any

    stages {

        stage('Clone') {

            steps {

                    git branch: 'main', url: 'https://github.com/vipulitinfra/flask-mysql-app.git'

            }

        }

        stage('Build') {

            steps {

                sh 'docker compose build'

            }

        }

        stage('Deploy') {

            steps {

                sh '''
                docker compose down || true
                docker compose up -d
                '''
            }

        }

    }
}
