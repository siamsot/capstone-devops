pipeline {
  agent any
  stages {
    stage('Create Cluster'){
        steps {
          withAWS(region:'us-east-1', credentials: 'full-access') {
            s3Upload(file:'index.html', bucket:'siamsot-jenkins', path:'index.html')
               }
           }
       }

}
}
