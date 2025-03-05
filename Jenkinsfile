pipeline {
    agent any 
    stages{
        stage ('clone'){
            steps{
                sh 'echo "code cloned"'
            }
        }
        stage ('test'){
            steps{
                sh 'echo "code scanned"'
            }
        }
        stage ('createfile'){
            steps{
                sh 'touch test-$BUILD_ID'
            }
        }
    }
    

}