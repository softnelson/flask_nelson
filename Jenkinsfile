
def link = 'http://'
def ip = 'teste'
def port = '5000'
//def tot =  link + port 


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
                script{    
                //sh "docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' nomeflask"
                
                    
                    ip = sh(returnStdout: true, script: "docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' nomeflask")
                    //sh 'docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' nomeflask; echo $? > status'
                    //def r = readFile('status').trim()
                
                    
                     //IP = sh "docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' nomeflask"
                    sh "echo ${ip}"
                    sh "echo ${link}" 
                    sh "echo ${port}"                 
                    sh "echo ${link}${ip}${port}"
                    //result = sh "echo ${ip}${tot}"

                    //sh 'curl -o -I -L -s -w "%{http_code}\n" ${link}${ip}'
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
