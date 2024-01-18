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
                sh 'docker build . -t manoj3214/rohith:latest'
            }
        }
        stage('Push'){
            steps{
              withCredentials([usernamePassword(credentialsId: 'manoj-dockerhub', passwordVariable: 'Manoj321@', usernameVariable: 'manoj3214')]) {
        	     sh "docker login -u ${env.manoj3214} -p ${env.Manoj321@}"
                 sh 'docker push manoj3214/rohith:latest'
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
