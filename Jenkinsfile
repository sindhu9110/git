pipeline {
  environment {
    registry = "saisriraviteja90/jenkins_pipelins"
    registryCredential = 'Docker_Id'
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/Raviteja1775/git.git'
      }
    }
    stage('Building image') {
      steps{
        sh 'docker build -t drupal:latest .
       
        sh 'docker tag drupal saisriraviteja90/drupal:$BUILD_NUMBER'
      }
    }
    stage('Deploy Image') {
      steps{
            withDockerRegistry([ credentialsId: "Docker_Id", url: "" ]) {
              sh  'docker push saisriraviteja90/jenkintest:latest'
        }
      }
    }
    
}
