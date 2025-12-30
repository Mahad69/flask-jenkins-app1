pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Mahad69/flask-jenkins-app1.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat '''
                python -m venv venv
                venv\\Scripts\\activate
                pip install --upgrade pip
                pip install -r requirements.txt
                '''
            }
        }

        stage('Run Unit Tests') {
            steps {
                bat '''
                venv\\Scripts\\activate
                pytest
                '''
            }
        }

        stage('Build Application') {
            steps {
                bat '''
                if not exist build mkdir build
                copy *.py build
                '''
            }
        }

        stage('Deploy Application') {
            steps {
                bat '''
                if not exist C:\\flask_deploy mkdir C:\\flask_deploy
                copy build\\* C:\\flask_deploy
                echo Deployment Successful
                '''
            }
        }
    }
}
