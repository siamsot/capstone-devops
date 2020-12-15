pipeline {
  agent any
  stages {
    stage('Create Cluster'){
        steps {
          withAWS(credentials: 'full-owner') {
            sh 'ansible-playbook ./infra-playbook.yml'
               }
           }
       }

}
}
