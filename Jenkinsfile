pipeline {
   agent any

   environment {
    AWS_REGION = 'us-east-2'
    IMAGE_ECR_REPO = '529088290671.dkr.ecr.us-east-1.amazonaws.com/jenkins_cicd'
    ECR_REPO = '529088290671.dkr.ecr.us-east-1.amazonaws.com'

   }

  stages{
    stage('CodeScan'){
        steps{
            sh 'trivy fs .  -o result.html'
       
           
        }
    }
    stage('dockerLogin'){
        steps{
            sh 'aws ecr get-login-password --region $AWS_REGION | docker login --username AWS --password-stdin $ECR_REPO'
            sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 529088290671.dkr.ecr.us-east-1.amazonaws.com'
        }
    }
    stage('dockerImageBuild'){
        steps{
            sh 'docker build -t jenkins_cicd .'
            sh 'docker build -t imageversion . '
        }
}
    stage('dockerImageTag'){
        steps{
            sh "docker tag jenkins-ci:latest $IMAGE_ECR_REPO:latest"
            sh "docker tag imageversion $IMAGE_ECR_REPO:v1.$BUILD_NUMBER"
        }    
        }
    
    stage('pushImage'){
        steps{
            sh 'docker push $IMAGE_ECR_REPO:lates'
            sh 'docker push $IMAGE_ECR_REPO:v1.$BUILD_NUMBER'
           
        }
    }
   } 
   }