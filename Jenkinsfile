pipeline {
    agent { label 'dev' }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Deploy Full Stack (Main)') {
            when {
                branch 'main'
            }
            steps {
                echo "Deploying Full Stack (main branch)..."
                sh 'docker compose down || true' // Stop previous compose, ignore errors if none
                sh 'docker compose up -d --build'
                echo "Full Stack is running."
            }
        }
    }
}
