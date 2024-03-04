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
                always { param ->
                    script {
                        // Add any additional test steps or checks here if needed
                    }
                }
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    // Push the new .cpp file to your repository
                    sh 'git add my_program.cpp'
                    sh 'git commit -m "Add new .cpp file"'
                    sh 'git push origin main'
                    echo 'Deployment Successful'
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
