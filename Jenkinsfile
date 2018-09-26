pipeline {
    agent any
	
	

    stages {
        stage ('Git Checkout') {

            steps {
               git credentialsId: '15df31c2-35d4-4cbe-af56-6ffdaf4170af', url: 'https://github.com/jyotirmoysha/jenkinspipelinescript.git'

                }
            }
			
			stage ('Maven Build') {

            steps {
					withMaven {
					            //for Linux
					            //sh 'mvn clean install'
					            //for windows
								bat 'mvn clean install'
                                echo 'War created successfully'
							}																				
												
            
			}
            }
			
			stage ('Maven Test run') {

            steps {
					withMaven {
					            //for Linux
					            //sh 'mvn test'
					            //for windows
								bat 'mvn test'
                                echo 'Test executed successfully'
							}																				
					
				}
            }
			
			
			
        }

       
    }
