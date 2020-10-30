pipeline {
 environment {
  registry="secchanakya/nav-test-repo"
  registryCredentials ="Navtoken"
  dockerImage=''
 }
 agent any
 
 stages {
  stage('Build Docer Image') {
   steps {
    script { 
     dockerImage = docker.build registry + ":BUILD_NUMBER"
       }
      }
    }
  
  stage ('Push to DockerHub') {
   steps {
    docker.withRegistry('',registryCredentials) {
     docker.Image.push()
    }
   }
  } 
 }  
  stage ('Test Run') {
   steps {
    sh 'docker run -d cyberfrat:$BUILD_NUMBER'
   }
  }
 }
}
