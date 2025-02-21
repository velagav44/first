pipeline {
    agent any
   /* environment{
        DOCKER_TAG = getDockerTag()
    }*/
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
          stage('Run Shell on Windows') {
            steps {
                bat '"C:\\Program Files\\Git\\bin\\bash.exe" -c "echo Hello from Git Bash!"'
                }
        }
          /*stage('Build Docker Image'){
            steps{
            /  sh "docker build . -t velavijay85/nodejs:${DOCKER_TAG}"
            }
        }*/
     }
}

/*
def getDockerTag(){
    def tag  = sh script: 'git rev-parse HEAD', returnStdout: true
    return tag
}

*/