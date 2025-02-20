pipeline {
    agent any
    stages {
         stage('Get Docker Tag') {
            steps {
                script {
                    // Get the Docker tag and store it in an environment variable
                    env.DOCKER_TAG = bat(script: 'git rev-parse HEAD', returnStdout: true).trim()
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                bat "docker build ."
            }
        }
    }
}

