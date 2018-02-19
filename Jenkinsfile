  pipeline {
   agent any   
   stages{
       stage('Build Docker Image') {
           agent {
               dockerfile {
                   reuseNode true                    
                   filename 'Dockerfile'
                   dir '.'
                   image: myfffff:latest
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
