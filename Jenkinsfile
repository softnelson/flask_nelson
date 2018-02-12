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
            agent {
                docker {
                  reuseNode true
                  image 'FLASK_APP=</path/to/file/containing/app/instance>.py'
              }
           }
            steps {
              echo 'done'
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
