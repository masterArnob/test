pipeline{
    agent any
    
// THIS LINE MAKES IT AUTO-RUN (every 30 seconds check)
    triggers {
        pollSCM 'H/30 * * * *'
    }
    
    environment{
        SSH_CREDENTIALS = 'my-ssh-private-key'
        REPOSITORY_URL = 'git@github.com:masterArnob/test.git'
        BRANCH_NAME = 'main'
        APP_NAME = 'checking'
    }
    
    stages{
        stage('cloning-repo'){
            steps{
                echo "start cloning..."
            
                sshagent(credentials: ["${SSH_CREDENTIALS}"]){
                    sh 'rm -rf ${APP_NAME}'
                    sh 'git clone --branch ${BRANCH_NAME} --single-branch ${REPOSITORY_URL} ${APP_NAME}'
                 }
                
                echo "clonnig finish..."
            }
        }
    }
}