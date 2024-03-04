pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    // Compile the .cpp file using a shell script
                    sh '''
                        g++ -o output YOUR_SRN-1.cpp
                    '''
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Run the compiled program and print its output
                    sh './output'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Push the changes to your repository
                    // Assuming you have your repository configured
                    // and authenticated already
                    // For example, you might use Git commands here
                    git push origin master
                }
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
