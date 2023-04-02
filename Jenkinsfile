pipeline {
   agent { node {label "maven" } }

   stages {
      stage('Test') {
         steps {
            sh './mnvw verify'
         }
      }
   }

}
