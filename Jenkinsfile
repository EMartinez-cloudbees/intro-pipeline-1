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
    stage('Testing') {
      parallel {
        stage('Java 8') {
          agent { label 'jdk9' } // note this doesn't matter :)
          steps {
            container('maven8') { // this is your environment
              sh 'mvn -v'
            }
          }
        }
        stage('Java 9') {
          agent { label 'jdk8' }
          steps {
            container('maven9') {
              sh 'mvn -v'
            }
          }
        }
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