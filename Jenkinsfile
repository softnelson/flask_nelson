
  pipeline {
   agent any   
   stages{
       stage('Build Docker Image') {
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
                  image 'flask_app'
				  args 'flask_app:1.0'
				 }
			}
		}
   }
   post {
       always {
           deleteDir()
       }
   }    
}
