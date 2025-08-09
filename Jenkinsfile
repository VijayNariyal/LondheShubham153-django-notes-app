@Library("sharedLibrary") _
pipeline {
    agent { label "agent vijay"}
    stages{
        stage("SharedLibrary"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                echo "This is Cloning the code from github"
                script{
                    cloneCode("https://github.com/VijayNariyal/LondheShubham153-django-notes-app.git","main")
                }
                echo "Code clone successfully"
            }
        }
        stage("Build"){
            steps{
                echo "This is Building the code"
                script{
                    docker_build("github-nodeapp","latest","181190101033")
                }
                echo "docker is build successfully you can run it now."
            }
        }
        stage("Push to DockerHub"){
            steps{
                echo "This is Pushing the image to DockerHub"
                script{
                    docker_push("github-nodeapp","latest","181190101033")
                }
                echo "This step is completed image pushed to DockerHub."
            }
        }
        stage("Deploy"){
            steps{
                echo "This is Deploying the code to test working"
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}
