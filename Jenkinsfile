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
                        sh 'wget -q -O - http://www.google.pt'          
               }
           }
        stage('test container') {
            steps {
                echo 'Testing....'
            }
       }
       
   }
   post {
       always {
           deleteDir()
       }
   }    
}
