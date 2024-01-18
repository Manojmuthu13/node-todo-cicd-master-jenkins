pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('manu-dochub')
    }
    
    stages{
        stage('Code'){
            steps{
                git url: 'https://github.com/Manojmuthu13/node-todo-cicd-master-jenkins.git', branch: 'master' 
            }
        }
        stage('Build and Test'){
            steps{
                sh 'docker build . -t manoj3214/node-todo-test:latest'
            }
        }
        stage("login"){
            steps{
                sh 'echo $DOCKERHUB_CREDENTIAL_PSW | docker login -u $DOCKERHUB_CREDENTIAL_USR --pas
            }
        }
        stage('Push'){
            steps{
                 sh 'docker push manoj3214/node-todo-test:latest'
                }
            }
        }
        stage('Deploy'){
            steps{
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}
