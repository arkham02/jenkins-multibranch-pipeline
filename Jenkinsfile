//This file shows the use of environment variables, local env variables
//the use of input and prompts
//the use of when for running a stage only on a specific branch
//at the very end - a new feature branch is created from master branch, and this comment is added to trigger the jenkins build on the new feature branch
// stage - can have have environment, stages, when, parallel 
pipeline{
    agent any
    environment {
        browser = 'chrome'
    }
    stages{
        stage('Build'){
            steps{
                echo 'Build the project ..'
            }
        }
        stage('Tests in parallel'){
            parallel{

                stage('API Tests'){
                    environment{
                      mylocalenvvariable = 'Running API tests ..'
                    }
                    steps{
                        echo "My local env variable message: ${mylocalenvvariable}"  //needs double qutes
                        echo 'My local env variable message:'+ mylocalenvvariable // no need to use ${}
                    }
                }

                stage('Sanity UI Tests'){
                    steps{
                        echo "Running Sanity tests on browser : ${browser}"
                    }
                }
            }
        }
        stage('Deploy to UAT'){
            when{
              branch 'master'
            }
            steps{
                input(message: 'Do you want to deploy to UAT ?', id: 'deployMsg')
                echo 'Deployment only to be done for master branch ..'
            }
        }
        
        stage('Notify'){
            steps{
              echo 'notifying'
            }
        }
    }
}
