pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                echo 'Clone App Repository'
                git 'https://github.com/eliud-kinyanjui/gallery'
                slackSend channel: 'eliud_ip1', color: 'good', message: 'Git Clone'
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