pipeline {
  agent any
  environment {
    DOCKER_TAG = getDockerTag()
  }
  stages {
    stage('Docker Build and Push') {
      steps {
        sh 'echo Welcome to Docker Build and Push'
      }
    }
    stage('Build Docker Image') {
      steps {
        sh script: "docker build . -t velavijay85/nodejs:${env.DOCKER_TAG}"
      }
    }
    stage('Docker Hub Push') {
      steps {
      withCredentials([string(credentialsId: 'docker-hub', variable: 'dockerHubPwd')]) {
        sh "docker login -u velavijay85 -p ${dockerHubPwd}"
        sh "docker push velavijay85/nodejs:${env.DOCKER_TAG}"
         }
      }
    }
  }
}

def getDockerTag() {
  def tag = sh script: 'git rev-parse HEAD', returnStdout: true
  return tag
}