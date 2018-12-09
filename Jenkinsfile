def workspace;
node(){
    stage('Clone repository'){
        
		checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/odiarra/testest.git']]])
    }  
    stage('Build image'){ 
		echo "Build the image"     
        def image = docker.build('odiarra/testest')  
    } 
          
    stage('Build image'){ 
            
        app = docker.build('odiarra/testest')  
    }  
    stage('Push image') {
    
    	docker.withRegistry('https://hub.docker.com/', 'dockerr-hub-credentials') {
        	app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
   }  
        
    stage('test container'){
    	steps {
                sh 'python -m py_compile ./tests/test_copy.py' 
        }
    }
   
}
