pipeline {
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
    stage('Deploy') {
      options {
        timeout(time: 60, unit: 'SECONDS')
      }
      input {
        message "Should we continue?"
      }
      steps {
        echo "Continuing with deployment"
      }
    }
  }
}