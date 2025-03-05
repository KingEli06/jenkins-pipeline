pipeline {
    agent any 
    stages{
        stage ('clone'){
            steps{
                sh 'echo "code cloned"'
            })
        }
        stage ('test'){
            steps{
                sh 'echo "code scanned"'
                sh 'cat /etc/os-release'
            }
        }
        stage ('createfile'){
            steps{
                sh 'touch text-$BUILD_ID'
            }
        }
    }
    

}