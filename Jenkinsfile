  pipeline {
   agent any   
   stages{
       stage('Build Docker Image') {
           agent {
               dockerfile {
                   docker { image 'maven:3-alpine' }
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
