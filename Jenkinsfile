pipeline {
  agent {
    label 'jdk9'
  }
  stages {
    stage('Say Hello') {
      steps {
        echo 'Howdy Earth!!'
        sh 'java -version'
      }
    }
  }
}