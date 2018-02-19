  pipeline {
   agent any   
   stages{
       stage('Build Docker Image') {
           agent {
               dockerfile {
                   reuseNode true                    
                   filename 'Dockerfile'
                   dir '.'
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
