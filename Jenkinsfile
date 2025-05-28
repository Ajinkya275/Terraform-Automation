pipeline {
    agent any
    tools {
        git 'DefaultGit'
    }

    environment {
        action = "apply"
    }

    stages {
        stage('Cloning github repo') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Ajinkya275/Terraform-Automation.git']])
            }
        }
    
        stage ("terraform init") {
             steps {
                 sh ("terraform init -reconfigure") 
             }
         }
        
        stage ("terraform Plan") {
            steps {
                sh ("terraform plan") 
            }
        }

        stage ("Action") {
            steps {
                echo "Terraform action is --> ${action}"
                sh ('terraform ${action} --auto-approve') 
           }
        }
    }
}
