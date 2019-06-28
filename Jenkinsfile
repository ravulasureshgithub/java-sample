pipeline{
    agent any
    stages {
        stage ('Initialize') {
            steps {
                ssh '''
                echo "PATH = ${PATH}"
                echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }

        stage ('Build'){
            steps {
                echo 'Hello Suresh'
            }
        }
    }
    
}
