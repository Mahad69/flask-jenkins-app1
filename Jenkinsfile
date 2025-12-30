pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Mahad69/flask-jenkins-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install --upgrade pip
                pip install -r requirements.txt
                '''
            }
        }

        stage('Run Unit Tests') {
            steps {
                sh '''
                . venv/bin/activate
                pytest
                '''
            }
        }

        stage('Build Application') {
            steps {
                sh '''
                mkdir -p build
                cp *.py build/
                '''
            }
        }

        stage('Deploy Application') {
            steps {
                sh '''
                mkdir -p /tmp/flask_deploy
                cp build/* /tmp/flask_deploy/
                echo "Deployment Successful"
                '''
            }
        }
    }
}
