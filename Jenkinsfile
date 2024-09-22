pipeline {
    agent any

    environment {
        NODE_HOME = tool name: 'NodeJS', type: 'NodeJSInstallation'
    }

    stages {
        stage('Checkout') {
            steps {
                // Clone the repository
                git 'https://github.com/ennded/JOB_SEEKING_BACKEND_DEPLOYMENT.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                // Install Node.js dependencies
                sh '${NODE_HOME}/bin/npm install'
            }
        }
        stage('Run Tests') {
            steps {
                // Run tests
                sh '${NODE_HOME}/bin/npm test'
            }
        }
        stage('Build') {
            steps {
                // Build the application (if needed)
                sh '${NODE_HOME}/bin/npm run build'
            }
        }
        stage('Deploy') {
            steps {
                // Deployment steps (e.g., deploy to a server)
                echo 'Deploying to server...'
                // Add your deployment commands here, e.g., using SSH or Docker
            }
        }
    }

    post {
        always {
            // Make sure this is inside a node block
            script {
                cleanWs()
            }
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the logs.'
        }
    }
}
