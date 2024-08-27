pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Cloning the repository from GitHub
                git branch: 'main', url: 'https://github.com/nikhilDkhot/jenkin'
            }
        }
        
       stage('Install Dependencies') {
            steps {
                // Installing Node.js dependencies
                echo 'Installing dependencies...'
                sh 'npm install'
            }
        }
        
        stage('Test') {
            steps {
                // Running tests (if you have any)
                echo 'Running tests...'
                sh 'npm test' // This assumes you have a test script defined in package.json
            }
        }
        
        stage('Build') {
            steps {
                // Building the application
                echo 'Building the application...'
                sh 'npm run build' // Optional if you have a build step in your project
            }
        }
        
        stage('Deploy') {
            steps {
                // Starting the Node.js application
                echo 'Deploying the application...'
                sh 'nohup node index.js &' // This will start the app in the background
            }
        }
    }
    
    post {
        always {
            // Clean up actions, logs, notifications, etc.
            echo 'Cleaning up...'
        }
        success {
            // Actions on successful pipeline run
            echo 'Pipeline completed successfully!'
        }
        failure {
            // Actions on failed pipeline run
            echo 'Pipeline failed. Check logs for errors.'
        }
    }
}