pipeline {
    agent any
    

    parameters {
        choice(name: 'ENV' , choices: ['dev', 'prod'], description: 'pick env') 
    }

    stages {
        stage('Terraform init') {
            steps {
                sh 'terraform init -backend-config=env-${ENV}/${ENV}-backend.tfvars'
            }
        }
    }

    stages {
        stage('Terraform plan') {
            steps {
                sh 'terraform plan -var-file=env-${ENV}/${ENV}.tfvars'
            }
        }
    }
}