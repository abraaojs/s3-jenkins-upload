pipeline {
  agent any
  stages {
    stage("Build") {
      steps {
        sh 'echo \'Build Test\''
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
          //s3Upload(bucket: 'abraao.stg.devsecops.com', workingDir:'build', includePathPattern:'**/*');
          //s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'file.txt', bucket:'abraao.stg.devsecops.com', path:'$pwd/file.txt')
          //s3Upload(bucket:"abraao.stg.devsecops.com", path:'/index.html', includePathPattern:'**/*', workingDir:'dist', excludePathPattern:'**/*.svg,**/*.jpg')
          //s3Upload(file:'index.html', bucket:'abraao.stg.devsecops.com', path:'$PWD/index.html')
          //s3Upload acl: 'Private', bucket: 'abraao.stg.devsecops.com', file: 'index.html'
          sh "aws s3 ls"
          sh "aws s3 cp index.html s3://abraao.stg.devsecops.com/"
          
        }
      }
    }
  }
}

