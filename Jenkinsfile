pipeline {
    agent any
    environment{
        DOCKER_TAG = getDockerTag()
    }
    stages {
        stage('Hello') {
            steps {
                sh 'echo Hello World' 
            }
        }
          stage('Print Docker Tag') {
            steps {
                  echo "The docker tag value is ${env.DOCKER_TAG}"
                }
        }
         stage('Build Docker Image'){
            steps{
                sh script: "docker build . -t velavijay85/nodejs:${env.DOCKER_TAG} " 
            }
        }
     }
}


def getDockerTag(){
    def tag  = sh script: 'git rev-parse HEAD', returnStdout: true
    return tag
}

