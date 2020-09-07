pipeline {
    agent any
    stages {
        stage('Build Dev stack') {
            steps {
            sh label: '', script: 'sh "aws cloudformation create-stack --stack-name dev-mediawiki --template-url https://github.com/arindam-cloud/demo/blob/master/mediawiki-deployment.yaml --parameters https://github.com/arindam-cloud/demo/blob/master/dev-parameters.json --region \'us-east-1\'"'
              }
             }
		stage('Build Prod stack') {
            steps {
            sh label: '', script: 'sh "aws cloudformation create-stack --stack-name prod-mediawiki --template-body file://mediawiki-deployment.yaml --parameters file://prod-parameters.json --region \'us-east-1\'"'
              }
             }
		stage('Output Dev-URL') {
            steps {
            sh label: '', script: 'sh "aws cloudformation --region us-east-1 describe-stacks --stack-name dev-mediawiki --query "Stacks[0].Outputs[?OutputKey==\'WebsiteURL\'].OutputValue" --output text"'
              }
             }
		stage('Output Prod-URL') {
            steps {
            sh label: '', script: 'sh "aws cloudformation --region us-east-1 describe-stacks --stack-name prod-mediawiki --query "Stacks[0].Outputs[?OutputKey==\'WebsiteURL\'].OutputValue" --output text"'
              }
             }
           }
         }
