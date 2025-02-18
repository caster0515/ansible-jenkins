pipeline {   
    agent any
    stages {
        stage("copy files to ansible server") {
            steps {
                script {
                    echo "copying all necessary files to ansible control node"
                    sshagent(['ansibel-server-key']) {
                        sh "scp -o StrictHostKeyChecking=no ansible/* root@35.158.123.151:/root"

                        withCredentials([sshUserPrivateKey(credentialsId: 'ec2-server-key', keyFileVariable: 'keyfile', usernameVariable: 'ec2-user')]) {
                            sh "scp ${keyfile} root@35.158.123.151:/root/test.pem"
                        }
                    }
                }
            }
        }
    }
} 
