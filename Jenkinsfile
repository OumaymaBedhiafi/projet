pipeline {
    environment { 

        DOCKERHUB_CREDENTIALS = credentials('oumaima12')
    }

    agent any

    stages {
        stage('Pull') {
            steps{
                script{
                    checkout([$class: 'GitSCM', branches:[[name:'*/master']],
                    userRemoteConfigs:[[
                        credentialsId: '77e0b9be-65c3-4e46-a8ac-0f9e6db1dac6',
                        url: 'https://github.com/OumaymaBedhiafi/projet.git']]])
                }
            }
        }
        stage('build') {
            steps{
                script{
		sh "npm install"
                sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"


                }
            }
        }
        stage('docker') {
            steps{
                script{
                sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml"


                }
            }
        }


	 stage('docker-registry') {
            steps{
                script{
                sh "ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml"


                }
            }
        }
    }
}
 
