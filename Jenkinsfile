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
        git([url: 'https://github.com/umairshah124/doc_jenk.git', branch: 'master', credentialsId: 'umairshah379'])

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
