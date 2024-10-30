pipeline { 
    agent any
    stages {
        
        stage('Clone') {
            steps {
                // Clone the GitHub repository with credentials
                git credentialsId: 'Org-GitHub-Token', url: 'https://github.com/mazingira-tech/FlaskNest.git'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                // Install Python dependencies listed in requirements.txt
                sh 'pip install -r requirements.txt'
            }
        }
        
        stage('Run Tests') {
            steps {
                // Run tests using pytest
                sh 'pytest'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                // Build Docker image for the Flask app
                sh 'docker build -t flaskr-app .'
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                // Deploy the Docker container to a staging environment
                sh 'docker run -d -p 5000:5000 flaskr-app'
            }
        }
    }
}

