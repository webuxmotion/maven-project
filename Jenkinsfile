pipeline {
  agent any
  tools {
    maven 'localMaven'
    jdk 'localJDK'
  }
  stages{
    stage ('Build'){
      steps {
        sh 'mvn clean package'
      }
    }   
  }
} 
  
