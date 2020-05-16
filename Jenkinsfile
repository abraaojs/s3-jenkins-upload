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
          //s3Upload(bucket: 'stgdatagate.superbid.net', workingDir:'build', includePathPattern:'**/*');
          //s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'file.txt', bucket:'stgdatagate.superbid.net', path:'$pwd/file.txt')
          //s3Upload(bucket:"stgdatagate.superbid.net", path:'/index.html', includePathPattern:'**/*', workingDir:'dist', excludePathPattern:'**/*.svg,**/*.jpg')
          //s3Upload(file:'index.html', bucket:'stgdatagate.superbid.net', path:'$PWD/index.html')
          //s3Upload acl: 'Private', bucket: 'stgdatagate.superbid.net', file: 'index.html'
          sh "aws s3 ls"
          sh "aws s3 cp index.html s3://stgdatagate.superbid.net/"
          
        }
      }
    }
  }
}

