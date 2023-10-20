pipeline {
    agent any

    tools{
        nodejs "nodejs"
    }
    stages {
        stage("Install Packages") {
            steps {
                script {
                    sh 'yarn install'
                }
            }
        }
        stage("Run App") {
            steps {
                script {
                    sh "pm2 stop todos-app 2> /dev/null"
                    sh 'pm2 start "yarn start" --name todos-app'
                    sleep 5
                }
            }
        }
        stage("Visit /health route") {
            steps {
                sh 'curl http://localhost:3000/health'
            }
        }
    }
}