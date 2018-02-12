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
      }
         stage {
                 stage('Build') {
                     steps {
                         echo 'Building...'
                         sh 'npm install'
                     }
                 }
           }
        stage('test container') {
            steps {
                sh 'echo exit | telnet localhost 5000'
            }
       }
       
   }
   post {
       always {
           deleteDir()
       }
   }    
}
