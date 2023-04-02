pipeline {
   agent { node {label "maven" } }

   stages {
      stage('Test') {
         steps {
            sh 'mvn verify'
         }
      }
   }

}
