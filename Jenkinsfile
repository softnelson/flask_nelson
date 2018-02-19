  pipeline {
   agent any   
   stages{
       stage('Build Docker Image') {
           agent {
               docker {
                   reuseNode true                    
                   image 'abc'
                   dir '.'
                   additionalBuildArgs '-t flask_app'
               }
           }
           steps {
               echo 'ls'
           }
       }
   }
   post {
       always {
           deleteDir()
       }
   }    
}
