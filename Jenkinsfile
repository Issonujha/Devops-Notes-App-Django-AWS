@Library("Shared") _
pipeline {
    agent {label "vinod"}
    
    stages {
        stage("Hello") {
            steps{
                script {
                    hello()
                }
            }
        }
        stage("Code") {
            steps{
                echo "Code is Cloning"
                // Already avaliable code that's why i skip it
                script {
                    clone("https://github.com/Issonujha/Devops-Notes-App-Django-AWS.git/", "master")
                }
            }
        }
        stage ("Build") {
            steps{
                echo "Code is building"
                sh "whoami"
                script {
                    docker_build("notes-app", "latest", "jhasonu")
                }
            }
        }
        stage("Test") {
            steps{
                echo "Code is in testing"
            }        
        }
        stage("Push To Docker") {
            steps {
                echo "Pushing Image to the Docker hub"
                docker_push("notes-app", "latest", "jhasonu")
            }
        }
        stage("deploy") {
            steps{
                // echo "Stopping any containers using port 8000..."
                // sh "docker ps -q --filter 'publish=8000' | xargs -r docker stop"
                // echo "Deploying the application..."
                // sh "docker run -d -p 8000:8000 notes-app:latest"
                // Old with run with images
                
                // No from docker compose.yml
                sh "docker compose up -d"
            }
        }
        
    }
}