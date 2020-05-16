pipeline {
  agent any
  stages {
    stage("Hello") {
      steps {
        sh 'echo \'Hello Shravan\''
      }
    }
    stage("Lint HTML") {
      steps {
        sh "tidy -q -e *.html"
      }
    }
    stage("Upload to AWS") {
      steps {
        withAWS(region:'sa-east-1',credentials:'s3-jenkins') {
          s3Upload(pathStyleAccessEnabled:true, payloadSigningEnabled: true, file:'index.html', bucket:'stgdatagate.superbid.net')
        }
      }
    }
  }
}

