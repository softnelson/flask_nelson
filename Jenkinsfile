
service_port = 9000  
mongo_port = 27017  
rabbit_port = 5672  

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
			docker build -t myDockerImage $WORKSPACE  
			docker run -d -p $service_port -p $mongo_port -p $rabbit_port myDockerImage  
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
