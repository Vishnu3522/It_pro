pipeline {
    agent any

    environment {
        SSH_PRIVATE_KEY = credentials('SSH_PRIVATE_KEY') // Use the correct credentials ID
        EC2_INSTANCE_IP = '54.234.116.55' // Replace with your EC2 instance's actual IP address
    }

    stages {
        stage('Deploy to EC2') {
            steps {
                script {
                    withCredentials([string(credentialsId: 'SSH_PRIVATE_KEY', variable: 'SSH_PRIVATE_KEY')]) {
                        sh '''
                            echo "$SSH_PRIVATE_KEY" > /tmp/private-key.pem
                            chmod 600 /tmp/private-key.pem
                            scp -i /tmp/private-key.pem -r ./path/to/your/website/files/* ubuntu@$EC2_INSTANCE_IP:/var/www/html/
                        '''
                    }
                }
            }
        }
    }
}
