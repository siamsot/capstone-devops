pipeline {
  agent any
  stages {
    stage('Create Cluster'){
        steps {
          withAWS(region:'us-east-1', credentials: 'full-owner') {
            sh 'ansible-playbook ./infra-playbook.yml'
               }
           }
       }

}
}
