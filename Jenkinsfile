pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/AditiAjitSalvi/DO_Practical_5.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dir('D:\FAMTMCA\SEM2\Devops\practicalno05') { // assuming Dockerfile and HelloWorld.java are in Q3 folder
                        docker.build("prac05q3", ".")
                    }
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    docker.image("prac05q3").run()
                }
            }
        }
    }
}
