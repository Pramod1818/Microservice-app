pipeline {
    agent {label 'dev'};

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Frontend') {
            when {
                branch 'frontend'
            }
            steps {
                echo "Building Frontend (frontend branch)..."
                sh 'cd frontend && docker build -t microservice-frontend:$BRANCH_NAME .'
            }
        }

        stage('Test Frontend') {
            when {
                branch 'frontend'
            }
            steps {
                echo "Testing Frontend (frontend branch)..."
                sh 'cd frontend && echo "Running frontend tests..."'
                sh 'cd frontend && sleep 3' // Simulate frontend tests 
                echo "Frontend tests completed."
            }
        }

        stage('Build Backend') {
            when {
                branch'backend'
            }
            steps {
                echo "Building Backend (backend branch)..."
                sh 'cd backend && docker build -t microservice-backend:$BRANCH_NAME .'
            }
        }

        stage('Test Backend') {
            when {
                branch 'backend'
            }
            steps {
                echo "Testing Backend (backend branch)..."
                sh 'cd backend && echo "Running backend tests..."'
                sh 'cd backend && sleep 5'
                echo "Backend tests completed."
            }
        }


        stage('Deploy Full Stack (Main)') {
            when {
                branch 'main'
            }
            steps {
                echo "Deploying Full Stack (main branch)..."
                sh 'docker compose down ' //stop privious compose
                sh 'docker compose up -d --build' 
                echo "Full Stack is running."
            }
        }


    }
}
