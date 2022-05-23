pipeline {
    environment {
        registry = "sindhuri9966/Sindhu9966"
        registryCredential = 'Docker_Id'
    }
    agent any
    stages {
        stage('Checkout') {
            steps {
                     // Get code from a GitHub repository
                    git url:'https://github.com/sindhu9110/git.git', branch: 'main',
                    credentialsId: 'Git'
            }
        }
        stage('Building image') {
            steps{
                sh 'docker build -t jenkintest:latest .'
                  sh 'docker tag jenkintest sindhuri9966/jenkintest:latest'
                sh 'docker tag jenkintest sindhuri9966/jenkintest:$BUILD_NUMBER'
            }
        }
        stage('Deploy our image') {
            steps {
                withDockerRegistry([ credentialsId: "Docker_Id", url: "" ]) {
              sh  'docker push sindhuri9966/jenkintest:latest'
              sh  'docker push sindhuri9966/jenkintest:$BUILD_NUMBER'
                }
            }
        }
    }
}
