pipeline {
  agent any
  stages {
    stage ('zip') {
      steps() {
        sh 'zip snesimylambda.zip mylambda.py'
      }
    }
    stage ('upload zip') {
      steps() {
        sh 'aws s3 cp target/snesimylambda.zip s3://sme-artifact-bucket/snesimylambda.zip --region us-west-2'
      }
    }     
  }
}