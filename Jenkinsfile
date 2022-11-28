pipeline {
		options { timestamps()}
		
		agent none
		stages {
		  stage('Check scm'){
		    agent any
		    steps{
		      checkout scm
		    }
                  }
		  stage('Build'){
		    steps{
		      echo "Building...${BUILD_NUMBER}"
                      echo "Building completed"
		    }
		  }
                  stage('Test'){
                    agent any
                      
                    steps {
                      
                      powershell 'pip install Flask'
                      powershell 'pip install xmlrunner'
                      powershell 'python3 test.py'
                    }
                    post{
                     always{
                       junit 'test-reports/*.xml'
                         }
                     success{
                       echo "Application testing successfully completed "
                     }
                     failure{
                       echo "Oooppss!!! Tests failed!"
                     }
                    }
                  }  
                }
              }
