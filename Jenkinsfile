@Library("Shared") _
pipeline {
    
    agent { label "vinod"}
    stages {
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage('code'){
            steps{
                script{    
                  clone("https://github.com/LondheShubham153/django-notes-app.git" , "main")
               }
            }
        }
        stage('Build'){
            steps{
                script{
                docker_build("notes-app" ,"latest" ,"raja423")
                }
            }
        }
        stage('push to docker hub'){
            steps{
                 script{
                    docker_push('notes-app' ,"latest" ,"raja423")
                }
            }
            
        }
        stage('Deploy'){
            steps{
                echo 'this is deploying code'
                sh 'docker run -d -p 8000:8000 notes-app:latest'
            }
        }
    }
}
