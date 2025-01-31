@Library("shared") _

pipeline{
    agent {label "agent"}
    stages{
        
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Clone Code"){
            steps{
                script{
                    clone("https://github.com/Karan90988/django-notes-app.git","dev")
                }
            }
        }
        stage("Build Code"){
            steps{
            script{
                docker_build("djongo-python-notes-app","latest","karan90988")
            }
            }
        }
        stage("push to dockerhub"){
            steps{
                script{
                    docker_push("djongo-python-notes-app","latest","karan90988")
                }
            }
        }
        stage("Deploy Code"){
            steps{
            echo "deploying the code"
            sh "docker compose down && docker compose up -d"
            }
        }
    }
}
