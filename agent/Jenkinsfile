pipeline {
    agent any

    stages {
        stage('CREDS') {
            steps {
               // This is accessing credential of type username and password
               withCredentials([usernamePassword(credentialsId: 'test_up', usernameVariable: 'USERNAME', passwordVariable: 'PASS')]) {
                    echo "$USERNAME $PASS"
                    sh '''
                        echo "$USERNAME $PASS"
                    '''
               }

                // This is accessing credential of type secret text
                withCredentials([string(credentialsId: 'secret_text', variable: 'SECRET_TEXT')]) {
                    echo "$SECRET_TEXT"
                    sh '''
                        echo "$SECRET_TEXT"
                    '''
               }

               // This is accessing credential of type secret file
                withCredentials([file(credentialsId: 'secret_file', variable: 'FILE_PATH')]) {
                    echo "$FILE_PATH"
                    sh '''
                        cat "$FILE_PATH"
                    '''
               }

                // This is accessing credential of type SSH username with private key
                withCredentials([sshUserPrivateKey(credentialsId: 'ssh_pem', usernameVariable: 'USER', keyFileVariable: 'SSH_KEY')]) {
                    echo "$USER $SSH_KEY"
                    sh '''
                        echo "$USER $SSH_KEY"
                    '''
               }
            }
        }
    }
}