pipeline {
    agent any
	tools {
    	   maven '3.6.3'
        }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
                //sh 'mvn deploy -s settings.xml'
            }
        }//end build
	    
        stage('Test') {
            steps {
                sh 'mvn test'
                junit 'target/surefire-reports/*.xml'
            }
        }//end of test	
	    
	stage('Sonar Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                sh 'mvn sonar:sonar' 
              }
            }
        }//end of sonar
      }//end stages
    }//end pipeline
