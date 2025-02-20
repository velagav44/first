pipeline {
    agent any
    environment {
        DOCKER_TAG = getDockerTag()
    }
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    def tag = getDockerTag()
                    bat "docker build -t vijay4444/nodeapp:${tag} ."
                }
            }
        }
    }
}

def getDockerTag() {
    return bat(script: 'git rev-parse HEAD', returnStdout: true).trim()
}
