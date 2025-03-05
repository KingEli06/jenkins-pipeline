pipeline {
    agent any 
    stages{
        stage ('CodeScan'){
            steps{
                sh 'trivy --version'
                sh 'trivy fs . -o result.html'
                sh 'cta result.hmtl'
                
            }
        }
        stage ('dockerImageBuild'){
            steps{
                sh 'docker -v'
            }
        }
        stage ('pushImage'){
            steps{
                sh 'docker ps'
            }
        }
    }
    

}