pipeline {
  agent any
  stages {
    stage('calculation prep') {
      steps {
        sh 'pwd'
        sh 'cd source/calculation-offer-service/CalculationServiceAPISolution'
        sh 'docker build -t $CALCULATION_SERVICE_IMAGE:latest -t $CALCULATION_SERVICE_IMAGE:$BUILD_NUMBER .'
        sh 'docker tag $CALCULATION_SERVICE_IMAGE:latest $ECR_ID/$CALCULATION_SERVICE_IMAGE:latest'
        sh 'docker tag $CALCULATION_SERVICE_IMAGE:$BUILD_NUMBER $ECR_ID/$CALCULATION_SERVICE_IMAGE:$BUILD_NUMBER'
        sh 'docker login --username $ECR_CREDENTIALS_USR --password $ECR_CREDENTIALS_PSW $ECR_ID'
        sh 'docker image prune -f'
        sh 'docker push $ECR_ID/$CALCULATION_SERVICE_IMAGE:latest'
        sh 'pwd'
      }
    }

  }
  environment {
    ECR_ID = '"ap-south-1"'
    CALCULATION_SERVICE_IMAGE = '"tickaramv2-casestudy-calculation-service"'
    ECR_CREDENTIALS = credentials('ecr-credentials')
  }
}