pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building step'
                sh 'DOCKER_BUILDKIT=1 docker build -t tehilla-cohen/todo-fe:latest -f DockerfilePipeline --target builder .'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing step'
                sh 'DOCKER_BUILDKIT=1 docker build -t tehilla-cohen/todo-fe:latest -f DockerfilePipeline --target testing .'
            }
        }
        stage('Delivery') {
            steps {
                echo 'Delivery step'
                sh 'DOCKER_BUILDKIT=1 docker build -t tehilla-cohen/todo-fe:latest -f DockerfilePipeline --target delivery .'
            }
        }
         stage('Cleanup') {
            steps {
                echo 'Cleanup the system'
                sh 'docker system prune'
            }
        }
         stage('Push') {
            steps {
                echo 'pushing to dockerhub'
                sh 'docker push tehillacohen/todo-fe:latest'
            }
        }
    }
}
