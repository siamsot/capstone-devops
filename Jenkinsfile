pipeline {
  environment {
    registry = "siamsot/capstone"
    registryCredential = "dockerhub_id"
    dockerImage = ''
  }
  agent any
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
          docker.withRegistry( '', 'dockerhub_id' ) {
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
    stage('Continuous Deployment to Cluster'){
      steps {
        sh 'sudo kubectl apply -f continuous_deployment.yml'
      }
    }
  }
}
