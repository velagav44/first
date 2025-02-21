pipeline {
    agent any
    environment{
        DOCKER_TAG = getDockerTag()
    }
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
          stage('Run Shell on Windows') {
            steps {
                   echo "The docker tag value is ${env.DOCKER_TAG}"
                }
        }
        /*
         stage('Build Docker Image'){
            steps{
               bat "docker build . -t velavijay85/nodejs:%DOCKER_TAG%" 
            }
        }*/
     }
}


def getDockerTag(){
    def tag = bat(script: 'git rev-parse HEAD', returnStdout: true)
    return tag
}

