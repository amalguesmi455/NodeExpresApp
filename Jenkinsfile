def dockerimage
pipeline {
    
     agent any
    
  tools {nodejs "NodeJs 18.4.0"}
    stages {
        
        stage('Deployer app node'){

          steps {
           echo 'test'
          }
        }
        
        stage('Build') {
          steps {
              
            sh 'npm --version'  
            sh 'npm install express'
            sh 'npm install mongo'
            sh 'npm install mocha -g'
            
          }
        }  
        /* stage('Test') {
          steps {
            sh 'npm test'
          }
        }*/
        stage('Build image with docker') {
             steps{
                script{
                   
                   dockerImage = docker.build("amalguesmi/appnode-oct:latest")
                    
                }
             }
                    
          }
        
       stage('Push image') {
  /* Finally, we'll push the image with two tags:
  * First, the incremental build number from Jenkins
  * Second, the 'latest' tag.
  * Pushing multiple tags is cheap, as all the layers are reused. */
  docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
    app.push("${env.BUILD_NUMBER}")
    app.push("latest")
  }
}
               
             
        
        
        
        /*stage('Docker Build and Push'){
            steps{
                withDockerRegistry([credentialsId: "docker-hub", url:""]){
                    //sh 'printenv'
                    sh 'docker build -t amalguesmi/appnode-oct:""$GIT_COMMIT"" .'
                    sh 'docker push amalguesmi/appnode-oct:""$GIT_COMMIT"" '
                }
            }
            
        }*/
        
         
        
    }
}
