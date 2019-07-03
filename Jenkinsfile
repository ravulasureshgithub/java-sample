pipeline {
    /*A declarative pipeline*/

    agent any
    tools {
    maven 'M3'
  }
    
    stages {
        
        stage ('Build Servlet Project') {



            steps {
                /*for Windows Machine*/    
                /*bat 'mvn clean package'*/

                 /*for Linux/MAC Machine*/    
                sh '''
                
                mvn clean package
                
                '''
            }
            post {
                success {
                echo 'Now Archiving......'

                archiveArtifacts artifacts : '**/*.war'
                        }  
            }

        }
        stage ('Deploy Build in Staging Area') {

            steps {

                build job : 'Deploy-StagingArea-Pipeline'
            }
        }
        stage ('Deploy to Production') {

            steps {
                timeout (time: 5, unit: 'DAYS'){
                    input message: 'Approve PRODUCTION Deployment?'
                }

                build job : 'Deploy_Production_Pipline'
            }
            post {
                success{
                    echo 'Deployment on PRODUCTION is Successful'
                }
                failure{
                    echo 'Deployment Failure on PRODUCTION'
                }
            }
        }
        
    }
    
    
}
