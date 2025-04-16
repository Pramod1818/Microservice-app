pipeline {
    agent { label 'dev' }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Backend') {
            steps {
                echo "Building Backend (backend branch)..."
                sh 'cd backend && docker build -t microservice-backend:$BRANCH_NAME .'
            }
        }

        stage('Test Backend') {
            steps {
                echo "Testing Backend (backend branch)..."
                sh 'cd backend && echo "Running backend tests..."'
                sh 'cd backend && sleep 5' // Simulate backend tests
                echo "Backend tests completed."
            }
        }

    }
}
