pipeline {   
    agent any
    stages {
        stage("copy files to ansible server") {
            steps {
                script {
                    echo "copying all necessary files to ansible control node"
                    sshagent(['ansibel-server-key']) {
                        sh "scp -o StrictHostKeyChecking=no ansible/* ubuntu@3.72.10.8:/root"

                        withCredentials([sshUserPrivateKey(credentialsId: 'ec2-server-key', keyFileVariable: 'keyfile', usernameVariable: 'ec2-user')]) {
                            sh "scp ${keyfile} ubuntu@3.72.10.8:/root/test.pem"
                        }
                    }
                }
            }
        }
    }
} 
