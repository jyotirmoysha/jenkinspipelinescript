pipeline {
    agent any
	
	environment {
        ENV_NAME = "${env.ENVIRONMENT_NAME}"
        MY_NAME = "${env.NAME}"
    }
	

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
            
            stage ('Move artefacts SSH') {

            steps {
                    echo 'Building Branch: ' + env.ENV_NAME
                    echo 'Building Branch: ' + env.MY_NAME
																									
					//bat move /-y "D:\example\original\*2007*.txt" "D:\example\New folder\"
					//bat move /y "C:/Users/js0e1608/.jenkins/workspace/my-first-jenkins-script" "E:/JenkinsProjLocationMaven/"
					// if (env.ENV_NAME == 'development') {
                        echo 'Building Container for development Branch: ' + env.ENV_NAME
                    //} else if (env.ENV_NAME == 'uat') {
                        echo 'Building Container for UAT Branch: ' + env.ENV_NAME
                    //}

			//bat move /-y "C:/JYO/Rough/loc1" "C:/JYO/Rough/loc2"
					
				}
            }
			
			stage('Copy Archive') {
			 steps {
				 script {
					 step ([$class: 'CopyArtifact',
					 projectName: 'cvs-jenkins-pipeline-test',
					 filter: "*.*",
					 target: 'C:/JYO/Rough/loc2']);
				 }
			 }
				
				
				
			}
	}

       
    }
