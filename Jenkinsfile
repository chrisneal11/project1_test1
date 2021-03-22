pipeline {

  environment {

    registry = “chrisneal11/project1”

    registryCredential = ‘dockerhub’

    dockerImage = ‘’

  }

  agent any

  stages {

    stage(‘Cloning Git’) {

      steps {

        git ‘https://github.com/SimplilearnDevOpsOfficial/DockerizeJenkins.git '

      }

    }

    stage(‘Building image’) {

      steps{

        script {

          dockerImage = docker.build registry + “:$BUILD_NUMBER”

        }

      }

    }

    stage(‘Deploy Image’) {

      steps{

        script {

          docker.withRegistry( ‘’, registryCredential ) {

            dockerImage.push()

          }

        }

      }

    }

  }

}


