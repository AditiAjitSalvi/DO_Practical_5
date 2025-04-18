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
                    // Ensure the directory path is correct and accessible from Jenkins agent
                    dir('D:/FAMTMCA/SEM2/Devops/practicalno05') { 
                        docker.build("prac05q3", ".")
                    }
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Ensure Docker container runs correctly in detached mode
                    docker.image("prac05q3").run("-d")  // Runs the container in detached mode
                }
            }
        }
    }

    post {
        always {
            // Clean up Docker container after execution (for Windows agents)
            script {
                bat 'docker container prune -f'
            }
        }
    }
}
