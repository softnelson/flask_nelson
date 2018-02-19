  pipeline {
   agent any   
   stages{
       stage('Build Docker Image') {
           agent {
               dockerfile {
                   reuseNode true                    
                   filename 'Dockerfile'
                   dir '.'
                   additionalBuildArgs '-t flask_app'
               }
           }
           steps {
              sh "./run-tests-in-docker.sh"
           }
       }
   }
   post {
       always {
           deleteDir()
       }
   }    
}
