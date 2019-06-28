pipeline {
    /*A declarative pipeline*/

    agent any
    
    stages {
        
        stage ('Build Servlet Project') {
    
            steps {
                /*for Windows Machine*/    
                bat 'mvn clean package'
            }
        }

        post ('Posting'){
            success{
                echo 'Now Archiving......'

                archiveArtifacts artifacts : '**/*.war'
            }

        }
        
    }
    
}
