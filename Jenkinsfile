pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building step'
                sh 'DOCKER_BUILDKIT=1 docker build -t tehilla2022/todo-fe:latest -f DockerfilePipeline --target builder .'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing step'
                sh 'DOCKER_BUILDKIT=1 docker build -t tehilla2022/todo-fe:latest -f DockerfilePipeline --target testing .'
            }
        }
        stage('Delivery') {
            steps {
                echo 'Delivery step'
                sh 'DOCKER_BUILDKIT=1 docker build -t tehilla2022/todo-fe:latest -f DockerfilePipeline --target delivery .'
            }
        }
         stage('Cleanup') {
            steps {
                echo 'Cleanup the system'
                sh 'docker system prune -f'
            }
        }
         stage('Push') {
            steps {
                echo 'pushing to front-end dockerhub'
                sh 'docker login -u ${username} -p ${password}'
                sh 'docker push tehilla2022/todo-fe:latest'
            }
        }
    }
}
