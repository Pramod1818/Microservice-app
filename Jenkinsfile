pipeline {
    agent { label 'dev' }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Frontend') {
            steps {
                echo "Building Frontend (frontend branch)..."
                sh 'cd frontend && docker build -t microservice-frontend:$BRANCH_NAME .'
            }
        }

        stage('Test Frontend') {
            steps {
                echo "Testing Frontend (frontend branch)..."
                sh 'cd frontend && echo "Running frontend tests..."'
                sh 'cd frontend && sleep 3' // Simulate frontend tests
                echo "Frontend tests completed."
            }
        }

    }
}
