pipeline {
    agent any
    
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
        stage('Push'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'manoj-dochub', passwordVariable: 'Manojkumar@', usernameVariable: 'manu-dockerhub')]) {
        	     sh "docker login -u ${env.manoj3214} -p ${env.Manoj321@}"
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
