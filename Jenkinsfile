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
    }
}
