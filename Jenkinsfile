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
            steps{
                script{
           
         //           withDockerRegistry([credentialsId: "docker-hub", url:""]){
           //         dockerImage.push()
             withCredentials([usernamePassword( credentialsId: 'docker-hub', usernameVariable: 'amalguesmi', passwordVariable: '22651530mama')]) {
        
sh ' docker login -u amalguesmi -p 22651530mama  '
                 // Push your image now
            sh "docker push amalguesmi/appnode-oct:latest"
                
        }
    }
                    
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
