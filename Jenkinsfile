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

        stage('Deploy to Heroku') {
            steps {
                echo 'Deploy App to Heroku'
                withCredentials([usernameColonPassword(credentialsId: 'heroku', variable: 'HEROKU_CREDENTIALS')]){
                    sh 'git push https://${HEROKU_CREDENTIALS}@git.heroku.com/young-mountain-18198.git master'
                }
            }
        }
    }
}