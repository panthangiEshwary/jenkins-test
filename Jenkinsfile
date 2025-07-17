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
            sh 'docker run -d -p 5000:5000 jenkins-demo-image'
        }
    }
}

    }
}

