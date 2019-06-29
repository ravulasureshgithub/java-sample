pipeline {
    /*A declarative pipeline*/

    agent any
    
    stages {
        
        stage ('Build Servlet Project') {
    
            steps {
                /*for Windows Machine*/    
                bat 'mvn clean package'
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
                timeout (time: 5, unit: 'Day'){
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
