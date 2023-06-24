pipeline {
    agent any

    environment {
        APP_LINK = 'https://young-mountain-18198-00c30b751509.herokuapp.com'
    }

    stages {
        stage('Clone Repository') {
            steps {
                echo 'Clone App Repository'
                git 'https://github.com/eliud-kinyanjui/gallery'
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
                sh 'npm run tests'
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
    post {
        success {
            slackSend(color: 'good', message: "Gallery App deployment successful. Job Name - ${JOB_NAME} | Build number ${BUILD_NUMBER} | link ${APP_LINK}")
        }

        failure {
            slackSend(color: 'danger', message: "Gallery App deployment faield. Job Name - ${JOB_NAME} | Build number ${BUILD_NUMBER}")
        }
    }
}