pipeline {
  environment {
    registry = "siamsot/capstone"
    registryCredential = "dockerhub_id"
    dockerImage = ''
  }
  agent { dockerfile true }
  stages {
    stage('Linting Dockerfile') {
      steps {
        sh '''docker run --rm -i hadolint/hadolint < Dockerfile'''
      }
    }
    stage('Build and Push Docker Image') {
      steps {
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
          docker.withRegistry( '', registryCredential ) {
                        dockerImage.push()
              }
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
