pipeline {
  agent any
  environment {
    GKE_CLUSTER = 'student-cluster'
    PROJECT_ID = 'devops-dev-439108'
    GKE_ZONE = 'us-central1-a'
    K8S_MANIFEST_PATH = 'manifests'
  }
  stages {

    stage('Deploy to GKE Cluseter') {
      steps {
        sh 'echo Deploy to GKE Cluseter'
      }
    }

    stage('Wait for Approval') {
            steps {
                input message: 'Deploy to GKE?', ok: 'Proceed'
            }
        }

    stage('Authenticate with Google Cloud') {
      steps {
        script {
        withCredentials([file(credentialsId: 'gcp-service-account', variable: 'GOOGLE_CLOUD_ACCOUNT')]) {
        sh 'gcloud auth activate-service-account --key-file="$GOOGLE_CLOUD_ACCOUNT"'
        sh 'gcloud config set project "$PROJECT_ID"'
        sh 'gcloud container clusters get-credentials "$GKE_CLUSTER" --zone "$GKE_ZONE" --project "$PROJECT_ID"'
        }
        }
      }
    }

    stage('Deploy to GKE') {
      steps {
        script {
          sh "kubectl apply -f ${K8S_MANIFEST_PATH}/Deployment.yaml"
          sh "kubectl apply -f ${K8S_MANIFEST_PATH}/Service.yaml"
        }
      }
    }
  }

  post {
    success {
      sh 'echo Deploymet is success '
    }
    failure {
      sh 'echo deployment is filure '
    }
  }
}