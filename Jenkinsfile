pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello!"'
                   }
         }
		 stage(‘Lint HTML’) {
      steps {
        sh ‘tidy -q -e *.html’
      }

     }
}
