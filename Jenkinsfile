pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            timestamps()
          }
        }

        stage('Set up env') {
          steps {
            input(message: 'Proceed?', id: 'p')
          }
        }

      }
    }

    stage('Test') {
      steps {
        echo 'testing mode'
      }
    }

  }
  environment {
    browser = 'chrome'
  }
}