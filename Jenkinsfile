  pipeline {
   agent any   
   stages{
       stage('Build Docker Image') {
         def flask_nelson = docker.build "flask_nelson"
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
