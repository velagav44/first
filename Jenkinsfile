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

    stage('Seup Environemnt')
    {
      steps {
        sh 'which python || which python3'
        sh 'python3 --version || python --version'
        sh 'gcloud config set core/python-executable $(which python3)'
      }
    }

    stage('Authenticate with Google Cloud') {
      steps {
        script {
        withCredentials([file(credentialsId: 'gcp-service-account', variable: 'GOOGLE_CLOUD_ACCOUNT')]) {
        sh 'gcloud auth activate-service-account --key-file="$GOOGLE_CLOUD_ACCOUNT"'
        sh 'gcloud container clusters get-credentials "$GKE_CLUSTER" --zone "$GKE_ZONE"'
        }

        }
      }
    }

    stage('Deploy to GKE') {
      steps {
        script {
          sh "kubectl apply -f $K8S_MANIFEST_PATH/Deployment.yaml"
          sh "kubectl apply -f $K8S_MANIFEST_PATH/Service.yaml"
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