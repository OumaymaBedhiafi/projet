pipeline {
    agent any
  tools 
  {NodeJS'16.14.2'}
   
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
                sh " ansible/build.yml -i ansible/inventory/host.yml"
                 
                    
                }
            }
        }
        
    }
}
