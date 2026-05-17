pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
        stage('Clean Previous Build') {
            steps {
                // Deletes the build folder if it exists
                sh 'rm -rf build'
            }
        }
        stage('Build with CMake') {
            steps {
                // Creates a build folder and compiles the app
                sh 'cmake -S . -B build'
                sh 'cmake --build build'
            }
        }
        stage('Run Tests') {
            steps {
                // Change into the build directory and execute ctest
                sh 'cd build && ctest --output-on-failure'
            }
        }
        post {
        success {
            // Archive the executable artifact
            archiveArtifacts artifacts: 'build/my_app', followSymlinks: false
            
            // Send success email
            mail to: 'vmarni@mtu.edu',
                 subject: "SUCCESS: Jenkins Build #${BUILD_NUMBER} - ${JOB_NAME}",
                 body: "Great news! The build and all automated tests passed successfully for build #${BUILD_NUMBER}.\n\nYou can access the pipeline here: ${BUILD_URL}"
        }
        
        failure {
            // Send failure email
            mail to: 'vmarni@mtu.edu',
                 subject: "FAILURE: Jenkins Build #${BUILD_NUMBER} - ${JOB_NAME}",
                 body: "Attention: The build or automated tests failed for build #${BUILD_NUMBER}.\n\nPlease check the logs immediately here: ${BUILD_URL}console"
        }  
    }
}
}