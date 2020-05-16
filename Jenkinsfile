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
          //s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'file.txt', bucket:'stgdatagate.superbid.net', path:'$pwd/file.txt')
          //s3Upload(bucket:"stgdatagate.superbid.net", path:'/index.html', includePathPattern:'**/*', workingDir:'dist', excludePathPattern:'**/*.svg,**/*.jpg')
          s3Upload(file:'index.html', bucket:'stgdatagate.superbid.net', path:'/*')
        }
      }
    }
  }
}

