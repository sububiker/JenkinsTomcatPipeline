node{

   def tomcatWeb = 'C:\tomcat\apache-tomcat-9.0.33-windows-x64\apache-tomcat-9.0.33\webapps'
   def tomcatBin = 'C:\tomcat\apache-tomcat-9.0.33-windows-x64\apache-tomcat-9.0.33\bin'
   def tomcatStatus = ''
   stage('SCM Checkout'){
     git 'https://github.com/sububiker/JenkinsTomcatPipeline.git'
   }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
      //def mvnHome =  tool name: 'maven-3', type: 'maven'   
      //bat "${mvnHome}\\bin\\mvn package"
      bat "mvn package"
      }
/*   stage ('Stop Tomcat Server') {
               bat ''' @ECHO OFF
               wmic process list brief | find /i "tomcat" > NUL
               IF ERRORLEVEL 1 (
                    echo  Stopped
               ) ELSE (
               echo running
                  "${tomcatBin}\\shutdown.bat"
                  sleep(time:10,unit:"SECONDS") 
               )
'''
   }*/
   stage('Deploy to Tomcat'){
     bat "copy target\\JenkinsTomcat.war \"${tomcatWeb}"
   }
      stage ('Start Tomcat Server') {
         sleep(time:5,unit:"SECONDS") 
         //bat "${tomcatBin}\\startup.bat"
         bat "C:\\Users\\heman\\Tomcat\\apache-tomcat-9.0.33-windows-x64\\apache-tomcat-9.0.33\\bin\\startup.bat"
         sleep(time:100,unit:"SECONDS")
   }
}
