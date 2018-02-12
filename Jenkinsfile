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
         stage('test in docker') {
            agent {
               docker {
                  image 'ubuntu:16.04'
                     reuseNode true
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
