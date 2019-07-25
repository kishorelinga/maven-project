pipeline {
   
   stage('Preparation') { // for display purposes
             
      mvnHome = tool 'localmaven'
   }
   stage('Build') {
        steps 
		{
			bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
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