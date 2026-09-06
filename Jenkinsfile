pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git branch: 'main', url:'https://github.com/VedantBansal07/flask-app'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                python3 -m venv venv
                source venv/bin/activate
                pip install -r requirements.txt
                '''
            }
        }

        stage('Run Flask Test') {
            steps {
                sh '''
                source venv/bin/activate
                python app.py &
                sleep 5
                curl localhost:5000
                '''
            }
        }
    }
}

