pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'Cloning repo...'
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t jenkins-demo-image .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Run container in background
                    sh 'docker run -d -p 5000:5000 --name jenkins-demo jenkins-demo-image'

                    // Wait for few seconds
                    sh 'sleep 10'

                    // Stop container
                    sh 'docker stop jenkins-demo'
                }
            }
        }
    }
}

