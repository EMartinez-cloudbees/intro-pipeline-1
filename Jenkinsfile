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
    stage('Get Kernel') {
      steps {
        script {
          try {
            KERNEL_VERSION = sh (script: "uname -r", returnStdout: true)
          } catch(err) {
            echo "CAUGHT ERROR: ${err}"
            throw err
          }
        }
      }
    }
    stage('Say Kernel') {
      steps {
        echo "${KERNEL_VERSION}"
      }
    }
    stage('Parallel steps') {
      failFast true
      parallel {
        stage('Java 8') {
          agent { label 'jdk8' }
          steps {
            sh 'java -version'
            sleep time: 10, unit: 'SECONDS'
          }
        }
        stage('Java 9') {
          agent { label 'jdk9' }
          steps {
            sh 'java -version'
            sleep time: 20, unit: 'SECONDS'
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