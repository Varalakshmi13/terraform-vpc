pipeline {
    agent any
    

    parameters {
        choice(name: 'ENV' , choices: ['dev', 'prod'], description: 'pick env') 
    }

    stages {
        stage('Terraform init') {
            steps {
                sh 'cp env-${ENV}/Terrafile . ; terrafile'
                sh 'terraform init -backend-config=env-${ENV}/${ENV}-backend.tfvars'
            }
        }

        stage('Terraform plan') {
            steps {
                sh 'terraform plan -var-file=env-${ENV}/${ENV}.tfvars'
            }
        }
    }

  
}