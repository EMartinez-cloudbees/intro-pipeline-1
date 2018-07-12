pipeline {
  agent {
    label 'jdk8'
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