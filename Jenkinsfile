pipeline {
  environment {
    registry = "umairshah379/mydockerrepo"
    registryCredential = 'umairshah379'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
git 'https://github.com/umairshah124/doc_jenk.git'
        withCredentials([usernamePassword(credentialsId: 'umairshah379', username: 'umairshah379', password: 'imrankhan123')]) {
        sh 'cf login some.awesome.url -u $USERNAME -p $PASSWORD'
        }
      }
}
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push("$BUILD_NUMBER")
             dockerImage.push

          }
        }
      }
    }
  }
}
