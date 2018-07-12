pipeline {
  // Setup
  agent {
    label 'jdk8'
  }
  parameters {
    string(name: 'Name', defaultValue: 'whoever you are',
      description: 'Who should I say hi to?')
  }
  environment {
    PLANET = "Kev's World"
    TEST_USER = credentials('test-user')
  }
  // Build
  stages {
    stage('Say Hello') {
      steps {
        echo "Howdy ${params.Name}, welcome to ${PLANET}!!"
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
    // stage('Deploy') {
    //   options {
    //     timeout(time: 60, unit: 'SECONDS')
    //   }
    //   input {
    //     message "Which Version?"
    //     ok "Deploy"
    //     parameters {
    //         choice(name: 'APP_VERSION', choices: "v1.1\nv1.2\nv1.3", description: 'What to deploy?')
    //     }
    //   }
    //   steps {
    //     echo "Deploying ${APP_VERSION}."
    //   }
    // }
  }
  // Actions
  post {
    aborted {
      echo 'OI ${params.Name}, why didn\'t you push my button?'
    }
  }
}