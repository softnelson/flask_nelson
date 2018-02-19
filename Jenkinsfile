  pipeline {
   agent any   
   stages{
       stage('Build Docker Image') {
           agent {
             docker { image 'maven:3-alpine' }
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
