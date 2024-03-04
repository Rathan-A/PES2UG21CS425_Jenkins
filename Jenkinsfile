pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Add commands to build the project here
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add commands to run tests here
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Add commands to deploy the application here
            }
        }
    }
    
    post {
        always {
            script {
                if (currentBuild.result == 'FAILURE') {
                    echo 'Pipeline failed'
                }
            }
        }
    }
}
