pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Getting source code'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building application'
                sh 'mkdir -p build'
                sh 'cp index.html build/'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing application'
                sh 'test -s build/index.html'
                sh 'grep -q "Hello from Jenkins CI/CD" build/index.html'
            }
        }

        stage('Package') {
            steps {
                echo 'Preparing deployment artifact'
                archiveArtifacts artifacts: 'build/**'
            }
        }
    }
}
