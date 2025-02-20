pipeline {
    agent any
    environment {
        // Set the path to the Git Bash executable
        SHELL = 'E:\\Git\\bin\\bash.exe' // Adjust this path based on your Git Bash installation location
    }
      stages{
         stage("Build Docker Image"){
            steps{
                sh "docker build -t vijay4444/nodeapp:1234"
            }
         }
      }
}

