pipeline {
  agent any
  tools {
    maven 'Maven3.5.4'
  }
  stages {
    stage ('build/test') {
      steps() {
        sh 'mvn clean package'
      }
    }
    stage ('zip') {
      steps() {
        sh 'zip snesimylambda.zip mylambda.py'
        sh 'aws s3 cp target/snesimylambda.zip s3://sme-artifact-bucket/snesimylambda.zip --region us-west-2'
      }
    }  
    stage ('deploy') {
      steps() {
        sh '''
          aws cloudformation create-stack --stack-name snesilambdastacktest --template-body file://mylambda.template --capabilities CAPABILITY_NAMED_IAM --region us-west-2
          aws cloudformation wait stack-create-complete --stack-name snesilambdastacktest --region us-west-2
          aws cloudformation describe-stack-events --stack-name snesilambdastacktest --region us-west-2 
        '''
      }
    }    
  }
}