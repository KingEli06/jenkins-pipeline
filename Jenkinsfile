pipeline {
    agent any 
    stages{
        stage('CheckScan'){
            steps{
                sh 'trivy --version'
                sh 'trivy fs . -o result.html'
                sh 'cat result.html'
            }
        }
        stage('dockerLogin'){
            steps{
                sh 'aws ecr get-login-password --region us-east-1 | \
                docker login --username AWS --password-stdin 529088290671.dkr.ecr.us-east-1.amazonaws.com'
            }
        }
        stage('dockerImageBuild'){
            steps{
                sh 'docker -v'
                sh 'docker build -t jenkins-ci .'
                sh 'docker build -t imageversion .'
            }
        }
        stage('dockertagImage'){
            steps{
                sh 'docker tag jenkins-ci:latest 529088290671.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci:latest'
                sh 'docker tag imageversion 529088290671.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci:v1.$BUILD_NUMBER'
            }
        }
         stage('dockerpushImage'){
            steps{
                sh 'docker push 529088290671.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci:latest'
                sh 'docker push 529088290671.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci:v1.$BUILD_NUMBER'
            }
        }
    }
}