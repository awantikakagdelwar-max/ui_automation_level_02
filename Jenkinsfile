pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat """
                python -m venv venv
                venv\\Scripts\\python -m pip install --upgrade pip
                cd ui_automation_level_02
                ..\\venv\\Scripts\\python -m pip install -r requirements.txt
                """
            }
        }

        stage('Run Tests') {
            steps {
                bat """
                cd ui_automation_level_02
                ..\\venv\\Scripts\\pytest --alluredir=reports
                """
            }
        }

        stage('Archive Report') {
            steps {
                archiveArtifacts artifacts: 'ui_automation_level_02/reports/**', fingerprint: true
            }
        }
    }
}
