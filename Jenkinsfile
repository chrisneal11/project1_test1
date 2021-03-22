pipeline {

  environment {

    registry = “chrisneal11/project1”

    registryCredential = ‘dockerhub’

    dockerImage = ‘’

  }

  agent any

  stages {

    stage(‘Cloning_Git’) {

      steps {

        git ‘https://github.com/SimplilearnDevOpsOfficial/DockerizeJenkins.git '

      }

    }

    stage(‘Building_Image’) {

      steps{

        script {

          dockerImage = docker.build registry + “:$BUILD_NUMBER”

        }

      }

    }

    stage(‘Deploy_Image’) {

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


