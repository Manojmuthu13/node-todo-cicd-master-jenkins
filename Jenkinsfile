pipeline {
    agent any


    environment {
        DOCKERHUB_CREDENTIALS = credentials('manu-dockerhub')
        dockerHubUser='manoj3214'
        dockerHubPassword='Manoj321@'
    }
    
    stages{
        stage('Code'){
            steps{
                git url: 'https://github.com/Manojmuthu13/node-todo-cicd-master-jenkins.git/', branch: 'master' 
            }
        }
        stage('Build and Test'){
            steps{
                sh 'docker build . -t manoj3214/vamika:latest'
            }
        }
        stage('Push'){
            steps{
                sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
                 sh 'docker push manoj3214/vamika:latest'
                }
            }
        stage('Deploy'){
            steps{
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}

