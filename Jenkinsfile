pipeline {
  agent any
  tools{
      maven "Maven3.5.4"
  }
  stages {
    stage ('zip') {
      steps() {
        sh 'zip snesimylambda.zip mylambda.py'
      }
    }
    stage ('upload zip') {
      steps() {
        sh 'aws s3 cp snesimylambda.zip s3://sme-artifact-bucket/snesimylambda.zip --region us-west-2'
      }
    }     
  }
}