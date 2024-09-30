@Library("Shared") _
pipeline{
    
    agent {label "vinod"}
    
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
                    clone()
                }
            }
        }
        stage("Build"){
            steps{
               script{
                   docker_build("notes-app","latest", "yeshid")
               }
            }
        }
        stage("Push to DockerHub"){
            steps{
               script{
                   docker_push("notes-app","latest", "yeshid")
               }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is Deploying the code"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
