pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello!"'
                   }
         }
	     stage('Security Scan') {
              steps { 
                 aquaMicroscanner imageName: 'alpine:latest', notCompleted: 'exit 1', onDisallowed: 'fail'
              }
         }         
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-east-2',credentials:'aws-static') {
                  sh 'echo "Uploading content"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'static-jenkins-pipeline')
                  }
              }
         }
     }
}
