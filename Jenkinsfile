pipeline {
  environment {
    registry = "siamsot/capstone"
    registryCredential = "dockerhub_id"
  }
  agent any
  stages {
    stage {
      steps {
        sh 'hadolint Dockerfile'
      }
    }
    stage('Build and Push Docker Image') {
      steps {
        withCredentials(dockerhub_id){
          sh 'ansible-playbook ./container-build.yml'
              }
          }
      }
    stage('Create Cluster'){
        steps {
          withAWS(credentials: 'full-owner') {
            sh 'ansible-playbook ./infra-playbook.yml'
               }
           }
       }
  }
  }
