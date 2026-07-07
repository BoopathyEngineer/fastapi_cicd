pipeline {
    agent any

    environment {
        AWS_REGION = 'us-east-1'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Terraform Init') {
            steps {
                sh 'terraform init -input=false'
            }
        }

        stage('Terraform Validate') {
            steps {
                sh 'terraform validate'
            }
        }

        // ── Checkov IaC Security Scan ─────────────────────────────────────
        stage('Checkov IaC Security Scan') {
            steps {
                sh '''
                    pip install checkov --quiet
                    checkov -d . \
                        --framework terraform \
                        --output cli \
                        --soft-fail \
                        --compact
                '''
            }
            post {
                always {
                    echo 'Checkov scan complete'
                }
            }
        }
        // ─────────────────────────────────────────────────────────────────

        stage('Terraform Plan') {
            steps {
                sh 'terraform plan -input=false -out=tfplan'
            }
        }

        stage('Terraform Apply') {
            when {
                branch 'main'
            }
            steps {
                sh 'terraform apply -input=false tfplan'
            }
        }
    }
}
