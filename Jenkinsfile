pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/awantikakagdelwar-max/ui_automation_level_02.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat """
                python -m venv venv
                venv\\Scripts\\pip install --upgrade pip
                venv\\Scripts\\pip install -r requirements.txt
                """
            }
        }

        stage('Run Tests') {
            steps {
                bat """
                venv\\Scripts\\pytest --alluredir=reports
                """
            }
        }

        stage('Archive Report') {
            steps {
                archiveArtifacts artifacts: 'reports/**', fingerprint: true
            }
        }
    }
}
