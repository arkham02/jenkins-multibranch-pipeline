pipeline {
  agent any
  stages {
    stage('Set up env') {
      parallel {
        stage('Set up env') {
          steps {
            input(message: 'Proceed?', id: 'p')
          }
        }

        stage('Build') {
          steps {
            echo 'building'
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