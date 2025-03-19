pipeline {
    agent any 
    stages{
        stage('CheckScan'){
            steps{
                sh 'trivy --version'
                sh 'trivy fs . -o result.html'
            }
        }
        stage('dockerImageBuild'){
            steps{
                sh 'docker -v'
            }
        }
        stage('pushImage'){
            steps{
                sh 'docker ps'
            }
        }
    }
}