pipeline {
  agent any
  stages {
    stage('calculation prep') {
      steps {
        sh 'echo "hello"'
      }
    }

  }
  environment {
    ECR_ID = '"ap-south-1"'
    CALCULATION_SERVICE_IMAGE = '"tickaramv2-casestudy-calculation-service"'
    ECR_CREDENTIALS = credentials('ecr-credentials')

    
  }
}
