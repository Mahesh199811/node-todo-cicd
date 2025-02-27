@Library("Shared") _
pipeline{
    agent { label "dev"};
    
    stages{
        stage("Code Clone"){
            steps{
                script{
                   clone("https://github.com/Mahesh199811/node-todo-cicd.git","master")
                }
            }
        }
         stage("Code Build"){
            steps{
                script{
                   code_build("docker build -t node-app .")
                }
            }
        }
        stage("Code Push to Docker"){
            steps{
                script{
                   code_push_docker("dockerHubCreds","node-app:latest")
                }
            }
        }
        stage("Deploy"){
            steps{
                sh "docker compose down && docker compose up -d --build"
            }
        }
    }
}
