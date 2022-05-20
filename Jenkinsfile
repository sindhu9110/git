pipeline {
    environment {
        registry = "saissriraviteja90/Ravi244"
        registryCredential = 'Docker_Id'
    }
    agent any
    stages {
        stage('Checkout') {
            steps {
                     // Get code from a GitHub repository
                    git url:'https://github.com/Raviteja1775/git.git', branch: 'main',
                    credentialsId: 'Git'
            }
        }
        stage('Building image') {
            steps{
                sh 'docker build -t jenkintest:latest .'
                  sh 'docker tag jenkintest saissriraviteja90/jenkintest:latest'
                sh 'docker tag jenkintest saissriraviteja90/jenkintest:$BUILD_NUMBER'
            }
        }
        stage('Deploy our image') {
            steps {
                withDockerRegistry([ credentialsId: "Docker_Id", url: "" ]) {
              sh  'docker push saissriraviteja90/jenkintest:latest'
              sh  'docker push saissriraviteja90/jenkintest:$BUILD_NUMBER'
                }
            }
        }
    }
}
