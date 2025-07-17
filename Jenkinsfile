pipeline {
    agent any

    parameters {
        choice(name: 'ENVIRONMENT', choices: ['dev', 'staging', 'prod'], description: 'Select environment')
        string(name: 'VERSION', defaultValue: '1.0.0', description: 'App version to deploy')
        booleanParam(name: 'DEPLOY', defaultValue: true, description: 'Deploy after build?')
    }

    stages {
        stage('Show Parameters') {
            steps {
                echo "➡ ENVIRONMENT: ${params.ENVIRONMENT}"
                echo "➡ VERSION: ${params.VERSION}"
                echo "➡ DEPLOY: ${params.DEPLOY}"
            }
        }

        stage('Build App') {
            steps {
                echo "🛠 Building version ${params.VERSION} for ${params.ENVIRONMENT} environment"
                sh 'sleep 2'
            }
        }

        stage('Deploy App') {
            when {
                expression { return params.DEPLOY == true }
            }
            steps {
                echo "🚀 Deploying version ${params.VERSION} to ${params.ENVIRONMENT} environment..."
                sh 'sleep 2'
                echo "✅ Deploy completed!"
            }
        }
    }
}

