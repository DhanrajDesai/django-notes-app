@Library("Shared") _
pipeline{
    
    agent { label "slave1"}
    
    stages{
        
        stage("Hello"){
            steps{
                script{
                    echo "Hello"
                }
            }
        }
        stage("Code"){
            steps{
               script{
                
                 git url: "https://github.com/LondheShubham153/django-notes-app.git", branch: "main"   
                //echo "DhanrajSCMPleaseeses"
                //clone("https://github.com/LondheShubham153/django-notes-app.git","main")
               }
                
            }
        }
        stage("Build"){
            steps{
                script{
                echo "building"
                    //build("latest")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    echo "Docker building"
                    //docker_push("latest","trainwithshubham")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
               // sh "docker compose down && docker compose up -d"
            }
        }
    }
}
