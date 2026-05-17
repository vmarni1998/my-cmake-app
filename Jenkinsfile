pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
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
