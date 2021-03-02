pipeline {
    agent any
    environment {
        DOCKER_HUB_REPO = "annaarakeyan/terraform"
        REGISTRY_CREDENTIAL = "dockerhub_id"
        
    }

    stages {
        stage('Clean Workspace and SCM Checkout'){
            steps {
                cleanWs()
                checkout scm                
            }
        }

        stage('Deploy to kubernetes'){
			steps{
				ansiblePlaybook credentialsId: 'Ansible_ssh', disableHostKeyChecking: true, installation: 'Ansible', playbook: 'playbook.yaml'
			}
		}
    
    }
}
