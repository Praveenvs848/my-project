pipeline {
    agent any

    environment {
        VIRTUAL_ENV = "${WORKSPACE}/venv"
        PYTHON_PATH = "${VIRTUAL_ENV}/bin/python"
        PIP = "${VIRTUAL_ENV}/bin/pip"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Praveenvs848/my-python-dashboard.git'
            }
        }

        stage('Set Up Python') {
            steps {
                script {
                    sh 'python3 -m venv venv'
                    sh '. venv/bin/activate && pip install -r requirements.txt'
                }
            }
        }

        stage('Run Flask App') {
            steps {
                script {
                    sh '. venv/bin/activate && nohup python app.py &'
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
