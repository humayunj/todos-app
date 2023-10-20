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
                    sh "pm2 delete todos-app || : && pm2 start 'yarn start' --name 'todos-app'"
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