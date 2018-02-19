  pipeline {
   agent any   
   stages{
       stage('Build Docker Image') {
           agent {
               dockerfile {
                   reuseNode true                    
                   filename 'Dockerfile'
                   dir '.'
                    env:
                   - name: JAVA_OPTS
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
