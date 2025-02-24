pipeline {
  agent any
  environment {
    DOCKER_HUB_REPO = 'velavijay85/nodejs'
    IMAGE_TAG = 'd50d7bdedf2680488abe0f8a87ca7b66407c5f4a'
    GKE_CLUSTER = 'student-cluster'
    PROJECT_ID = 'devops-dev-439108'
    GKE_ZONE = 'us-central1-a'
    K8S_MANIFEST_PATH = 'manifests'
  }
  stages {
   
    stage('Docker Build and Push') {
      steps {
        sh 'echo Welcome to Docker Build and Push'
      }
    }
    /*
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
    }*/
  }
}

/*
def getDockerTag() {
  def tag = sh script: 'git rev-parse HEAD', returnStdout: true
  return tag
}
*/