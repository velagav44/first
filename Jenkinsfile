pipeline {
    agent any
    environment{
        DOCKER_TAG = getDockerTag()
    }
    stages {
          stage('Print Name'){
            steps{
                echo 'My name is vijay'
            }
        }
          stage('Build Docker Image'){
            steps{
                sh "docker build . -t velavijay85/nodejs:${DOCKER_TAG}"
            }
        }
     }
}

def getDockerTag(){
    def tag  = sh script: 'git rev-parse HEAD', returnStdout: true
    return tag
}
