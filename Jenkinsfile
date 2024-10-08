@Library("shared") _
pipeline{
    
    agent { label "slave1"}
    
    stages{
        
        stage("Hello shared"){
            steps{
                script{
                    hello.call()
                }
            }
        }
        stage("git cloning repo"){
            steps{
               script{
                // git url: "https://github.com/DhanrajDesai/django-notes-app.git", branch: "main"   
                   clone.clone("https://github.com/DhanrajDesai/django-notes-app.git","main")
               }
                
            }
        }
        stage("Build Images"){
            steps{
                script{
                   echo "building"
                   sh "docker build . -t djangolatest8:latest"
                    //build("latest")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    echo "Docker building"
                    withCredentials([usernamePassword(
                        credentialsId:"dockerhubcred",
                        passwordVariable:"dockerhubpass",
                        usernameVariable:"dockerhubuser"
                    )]){
                         sh " docker login -u ${env.dockerhubuser} -p ${env.dockerhubpass} "
                         sh " docker image tag djangolatest8:latest ${env.dockerhubuser}/djangolatest8:latest "
                        sh  " docker push ${env.dockerhubuser}/djangolatest8:latest "
                    }
                    
                    //docker_push("latest","trainwithshubham")
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
