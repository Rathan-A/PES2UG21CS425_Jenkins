pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    // Compile the .cpp file
                    sh 'g++ -o my_program my_program.cpp'
                    echo 'Build Stage Successful'
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    // Run the compiled program and print its output
                    sh './my_program'
                    echo 'Test Stage Successful'
                }
            }
            post {
                always {
                    script {
                        // Add any additional test steps or checks here if needed
                        echo 'Running additional test steps or checks...'
                        // Example: Run a shell command
                        sh 'echo "Additional tests completed"'
                    }
                }
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    try {
                        // Push the new .cpp file to your repository
                        sh 'git add my_program1.cpp'
                        sh 'git commit -m "Add new .cpp file"'
                        sh 'git push origin main'
                        echo 'Deployment Successful'
                    } catch (Exception e) {
                        echo "Deployment Failed: ${e.message}"
                        currentBuild.result = 'FAILURE'
                        error 'Deployment failed'
                    }
                }
            }
        }
    }
    
    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}
