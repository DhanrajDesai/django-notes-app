@Library("Shared") _
pipeline{
    
    agent { label "slave1"}
    
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
                echo "DhanrajSCMPleaseeses"
                clone("https://github.com/LondheShubham153/django-notes-app.git","main")
               }
                
            }
        }
        stage("Build"){
            steps{
                script{
                build("latest")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("latest","trainwithshubham")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
