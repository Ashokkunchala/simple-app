pipeline{
  agent any
  tools {
  maven 'maven3'
}
  stages{
    stage("SCM Checkout"){
      steps{
        git credentialsId: '5243e135-536c-499f-9a11-b08bf8cdfe8f', 
          url: 'https://github.com/deepashre/simple-app.git'
      }
    }
    stage("Maven Build"){
      steps{
        sh'mvn clean package'
      }
    }
    stage("Dev-Deploy"){
      steps{
        sshagent(['Tomcat_server-1']) {
        sh "scp -o StrictHostKeyChecking=no target/simple-app-3.0.0-SNAPSHOT.war ec2-user@172.31.81.33:/opt/tomcat/webapps/simple-app.war"
        sh "ssh ec2-user@172.31.81.33 /opt/tomcat/bin/shutdown.sh"
        sh "ssh ec2-user@172.31.81.33 /opt/tomcat/bin/startup.sh"
       }   
    }
  }
}
}
        
