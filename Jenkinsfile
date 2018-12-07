#!/usr/bin/env groovy

properties([
    buildDiscarder(logRotator(numToKeepStr: '5', artifactNumToKeepStr: '5')),
    pipelineTriggers([[$class:"SCMTrigger", scmpoll_spec:"H/15 * * * *"]]),
])
node('image docker'){
    
    def app 

    stage('Clone repository'){
        
        checkout scm   
    }        
    stage('Build image'){ 
            
        app = docker.build('odiarra/testest')  
    }  
    stage('Push image') {
         /* je push l'image * /
    
    	docker.withRegistry('https://hub.docker.com/', 'dockerr-hub-credentials') {
        	app.push("${env.BUILD_NUMBER}")
            app.push("latest")
   }  
        
    stage('test container'){
    	steps {
                sh 'python -m py_compile ./tests/test_copy.py' 
        }
    }
   
}
