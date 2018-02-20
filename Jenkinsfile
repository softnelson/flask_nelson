pipeline {
   agent any  
   stages{
       stage('Build Docker Image ') {
           agent {
               dockerfile {
                   reuseNode true                    
                   filename 'Dockerfile'
                   dir '.'
                   additionalBuildArgs '-t flask_app'
               }
           }
           steps {
               echo 'ls'
           }
        }
        stage('create container'){
             steps {
                        sh 'docker run -d --name nomeflask flask_app 5000:5000'
            
               }
           }
        stage('test container') {
            steps {
               curl -o -I -L -s -w "%{http://www.google.com}\n"
            }
       }
       
   }
   post {
       always {
           deleteDir()
       }
   }    
}
