@Library("Shared") _
pipeline {
    agent { label "vinod" }
    
    stages {
        stage("hello"){
            steps{
                script{
                     hello()
                }
            }
        }
        stage('code') {
            steps {
                script{
                    clone( "https://github.com/devagya-rattan/django-notes-app", "main")
                }
               
               
            }
        }
        stage('Build') {
            steps {
               docker_build("notes-app","latest","devagya-rattan")
            }
        }
        stage("Push to DockerHub") {
            steps {
                docker_push("notes-app","latest","devagyarattan")
            }
        }
        stage('this is deploying app') {
            steps {
                echo 'Deploying...'
                sh "docker compose up -d"
            }
        }
    }
}
