pipeline {
  // Setup
  agent {
    label 'jdk8'
  }
  environment {
    PLANET = "Kev's World"
    TEST_USER = credentials('test-user')
  }
  // Build
  stages {
    stage('Say Hello') {
      steps {
        echo "Howdy, welcome to ${PLANET}!!"
        echo "${env.BUILD_ID}"
        echo "${TEST_USER_USR}"
        echo "${TEST_USER_PSW}"
        sh 'java -version'
      }
    }
  }
  // Actions
  post {
    success {
      echo "Yay"
    }
  }
}