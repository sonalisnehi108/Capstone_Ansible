pipeline {
    agent any

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
                sh '''
                sudo cp index-aws.html /var/www/html/index.html
                sudo systemctl restart nginx
                '''
            }
        }

        stage('Deploy to Azure') {
            steps {
                sh '''
                sudo cp index-azure.html /var/www/html/index.html
                sudo systemctl restart nginx
                '''
            }
        }
    }
}
