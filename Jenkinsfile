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
                        sh 'docker run -d --name nomeflask flask_app -p 5000:5000'
            
               }
           }
        stage('test container') {
            steps {
                
                //sh "docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' nomeflask"
                
                    
                    //IP = $("docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' nomeflask")
                    //sh 'docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' nomeflask; echo $? > status'
                    //def r = readFile('status').trim()
                script{    
                    
                IP = sh "docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' nomeflask"
                   
                    sh "echo ${IP}"
                    //sh "echo $IP"
                    //sh "echo '$IP'"
                            RESPONSE=$(curl -o -I -L -s -w "%{http_code}\n" $IP')
                                       CODE=$(echo "$RESPONSE" | sed -n '$p')
                                    BODY=$(echo "$RESPONSE" | sed '$d')
                                    echo "$BODY"
                            
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
