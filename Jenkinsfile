environment {
  browser = 'chrome'
}
pipeline{
    agent any
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
                        echo '${mylocalenvvariable}'
                    }
                }

                stage('Sanity UI Tests'){
                    steps{
                        echo 'Running Sanity tests on browser : ${browser}'
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
    }
}