@Library("Shared") _
pipeline{
    
    agent{ label "swain" }
    
    stages{
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                 clone("https://github.com/Sumantswain/Django-notes-app.git","dev")
                }
             }
         }
         stage("Build"){
             steps{
                 script{
                     docker_build("notes-app","latest","sumantswain")
                 }
                
             }
         }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app", "latest","sumantswain")
                }
            }
        }
        stage("Deploy"){
            steps{
                sh "docker compose down && docker compose up -d "
            }
        }
    }
}
