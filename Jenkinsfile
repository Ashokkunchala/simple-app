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
  }
}
        
