pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git url: 'https://github.com/PankajaDesai/flask-devops-project.git', branch: 'main'
            }
        }

	stage('Install Requirements') {
            steps {
                sh 'pip install --break-system-packages -r app/requirements.txt'
            }
        }


        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-devops-app ./app'
            }
        }

        stage('Deploy Placeholder') {
            steps {
                echo 'Terraform / Ansible / Kubernetes deployment will go here later.'
            }
        }
    }
}
