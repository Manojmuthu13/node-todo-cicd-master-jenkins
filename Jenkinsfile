pipeline {
    agent any
    
    stages{
        stage('Code'){
            steps{
                git url: 'https://github.com/Manojmuthu13/node-todo-cicd-master-jenkins.git' 
            }
        }
        stage('Build and Test'){
            steps{
                sh 'docker build . -t manoj3214/rehane:latest'
            }
        }
        stage('Push'){
            steps{
               withCredentials([usernamePassword(credentialsId: 'manoj-dockerhub', passwordVariable: 'virat1234', usernameVariable: 'dockerhub')]) {
        	     sh "docker login -u ${env.dockerhub} -p ${env.virat1234}"
                 sh 'docker push manoj3214/rehane:latest'
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
