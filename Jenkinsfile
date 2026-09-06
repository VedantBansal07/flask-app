pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/VedantBansal07/flask-app'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                python3 -m venv venv
                ./venv/bin/pip install -r requirements.txt
                '''
            }
        }

        stage('Run Flask Test') {
            steps {
                sh '''
                ./venv/bin/python app.py &
                sleep 5
                curl localhost:5000
                '''
            }
        }
    }
}
