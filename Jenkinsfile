pipeline{
    agent any
    environment{
        image = 'rjram/web'
    }
    stages{
        stage('Checkout'){
            steps{
                git branch: 'main',url: 'https://github.com/Rjram-10/file.git'
            }
        }
        stage('Build Image'){

            steps{
                script{
                    docker_image = docker.build("${image}:latest")
                }
            }

        }
        stage('Deploy to hub'){
            steps{
                script{
                    docker.withRegistry('https://index.docker.io/v1/','DockerHUB'){
                       docker_image.push();
                    }
                }
            }
        }

        stage("Final"){
            steps{
            echo 'Hello, Jenkins! This is my first pipeline.'
        }}
    }
}
