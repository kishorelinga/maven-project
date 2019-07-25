pipeline {
   environment
   {
     mvnHome = tool 'localmaven'
   }
   agent {
   label 'master'
   }
   stages {
   stage('Checkout'){
   steps 
		{
			git changelog: false, poll: false, url: 'https://github.com/kishorelinga/maven-project.git'
   
		}
   }
   stage('Build') {
        steps 
		{
			bat "${mvnHome}\\bin\\mvn clean package"
		}
         
     
   }
   stage('Deploy') {
	steps {
	   bat '''cd C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\bin
            shutdown.bat'''
      fileOperations([fileCopyOperation(excludes: '', flattenFiles: false, includes: '*.war', targetLocation: 'C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\webapps')])
       bat '''cd C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\bin
        startup.bat'''
	}
    
   }
   }
}