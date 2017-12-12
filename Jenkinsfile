pipeline {
    agent {
        // docker { image 'maven:3.3.3' }
        // docker { image 'node:6.3' }
        // docker { image 'node:7-alpine' }
        // docker { image 'ruby' }
        // docker { image 'python:3.5.1' }
        docker { image 'php' }
    }
    stages {
        stage('Test') {
            steps {
                // sh 'mvn --version'
                // sh 'npm --version'
                // sh 'node --version'
                // sh 'ruby --version'
                // sh 'python --version'
                sh 'php --version'
            }
        }
    }
}