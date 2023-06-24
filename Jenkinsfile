pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                echo 'Clone App Repository'
            }
        }
        stage('Install Dependancies') {
            steps {
                echo 'Run npm install'
                sh 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                echo 'Run npm run test'
                sh 'npm run test'
            }
        }
    }
}