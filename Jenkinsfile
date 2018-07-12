pipeline {
  agent {
    label 'jdk8'
  }
  environment {
    MY_NAME = 'Kev'
    TEST_USER = credentials('test-user')
  }
  stages {
    stage('Say Hello') {
      steps {
        echo "Howdy ${MY_NAME}!!"
        echo "${env.BUILD_ID}"
        echo "${TEST_USER_USR}"
        echo "${TEST_USER_PSW}"
        sh 'java -version'
      }
    }
  }
}