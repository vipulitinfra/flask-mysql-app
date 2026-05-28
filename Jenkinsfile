pipeline {

    agent any

    stages {

        stage('Clone Repository') {

            steps {
                 git url: 'https://github.com/vipulitinfra/flask-mysql-app.git',
                    branch: 'main'

            }

        }

        stage('Build Containers') {

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
