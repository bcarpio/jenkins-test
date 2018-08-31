def awesomeVersion = 'UNKNOWN'
pipeline {
  agent {
    docker {
        reuseNode true
        image 'bcarpio/terraform-kitchen'
        label 'docker'
    }
  }
  options {
    buildDiscarder(logRotator(numToKeepStr: '10'))
  }
  stages {

    stage('get version') {
      steps {
        script {
          awesomeVersion = sh(returnStdout: true, script: 'echo 0.0.1')
        }
      }
    }
    stage('echo version') {
      steps {
        echo "awesomeVersion: ${awesomeVersion}"
      }
    }
  }

  post {
    always {
      deleteDir()
      cleanWs()
    }
  }
}
