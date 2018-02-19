  pipeline {
   agent any   
   stages{
       stage('Build Docker Image') {
           agent {
               dockerfile {
                   image 'flask_nelson' 
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
