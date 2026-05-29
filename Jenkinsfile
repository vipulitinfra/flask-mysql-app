pipeline {

    agent any

    stages {

        stage('Clone') {

            steps {

                git 'https://github.com/yourname/flask-mysql-app.git', git branch: 'main'

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
