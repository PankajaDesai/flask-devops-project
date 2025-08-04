pipeline {
    agent any

    environment {
        DOCKERHUB_IMAGE = "pankajadesai7/flask-devops-app"
    }

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

        stage('Push to DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    sh '''
                        echo "$DOCKER_PASSWORD" | docker login -u "$DOCKER_USERNAME" --password-stdin
                        docker tag flask-devops-app $DOCKERHUB_IMAGE
                        docker push $DOCKERHUB_IMAGE
                    '''
                }
            }
        }

        stage('Deploy Placeholder') {
            steps {
                echo 'Terraform / Ansible / Kubernetes deployment will go here later.'
            }
        }
    }
}

