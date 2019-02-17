
properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '4'))])

node{
    
  stage('Checkout the code') 
    {
     //git branch: 'master', credentialsId: '05b3cf19-8d8a-4ad0-ab66-0ac06671d09e', url: 'https://github.com/MithunTechnologiesDevOps/maven-web-application.git'   
     checkout scm
    }
    
   
    stage('Run Unit Test cases')
    {
      if(isUnix()){
       sh  'mvn test'
        }
        else{
           bat  'mvn test' 
        }
    }
    
    stage('Create Package')
    {
      if(isUnix()){
       sh  'mvn clean package'
        }
        else{
           bat  'mvn clean package' 
        }
    }
    
    stage('SonarQube Report')
    {
      if(isUnix()){
       sh  'mvn sonar:sonar'
        }
        else{
           bat  'mvn sonar:sonart' 
        }
    }
   /* 
    stage('Upload artifact into Nexus')
    {
      if(isUnix()){
       sh  'mvn deploy'
        }
        else{
           bat  'mvn deploy' 
        }
    }
    stage('Deploy app into Tomcat Server')
    {
      sh 'echo "App Deploymemt started"'  
      sh  'cp $WORKSPACE/target/*.war  /Users/mithunreddy/MithunTechnologies/Softwares/Running/apache-tomcat-9.0.13/webapps/'
      sh  'echo App deployed successfully'

    }
    */
    stage('Send Notifications')
    {
        
      mail bcc: 'rajeshchilukuri.tech@gmail.com', body: '''Build Done.
Regards,
Jenkins Build System Vagrant.
''', cc: 'rajeshchilukuri.tech@gmail.com', from: '', replyTo: '', subject: 'Build Done', to: 'rajeshchilukuri.tech@gmail.com'
  
    }
    
}
