pipeline {
   def mvnHome
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/kishorelinga/maven-project']]])
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'localmaven'
   }
   stage('Build') {
     
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
     
   }
   stage('Deploy') {
       bat '''cd C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\bin
            shutdown.bat'''
      fileOperations([fileCopyOperation(excludes: '', flattenFiles: false, includes: '*.war', targetLocation: 'C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\webapps')])
       bat '''cd C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\bin
        startup.bat'''
   }
}