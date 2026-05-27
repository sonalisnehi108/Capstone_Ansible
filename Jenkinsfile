pipeline {
    agent any
    environment {
        AWS_HOST = "ubuntu@3.239.23.15"
        AZURE_HOST = "ubuntu@172.191.94.139"
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/sonalisnehi108/Capstone_Ansible.git',
                    credentialsId: 'github-creds'
            }
        }

        stage('Deploy to AWS') {
            steps {
                sshagent(['aws-ssh-creds']) {
                    sh '''
                    scp index-aws.html $AWS_HOST:/var/www/html/index.html
                    ssh $AWS_HOST "sudo systemctl restart nginx"
                    '''
                }
            }
        }

        stage('Deploy to Azure') {
            steps {
                sshagent(['azure-ssh-creds']) {
                    sh '''
                    scp index-azure.html $AZURE_HOST:/var/www/html/index.html
                    ssh $AZURE_HOST "sudo systemctl restart nginx"
                    '''
                }
            }
        }
    }
}
