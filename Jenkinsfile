pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building step'
                sh 'DOCKER_BUILDKIT=1 docker build -t tehilla-cohen/todo-fe:latest --target builder .'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing step'
                sh 'DOCKER_BUILDKIT=1 docker build -t tehilla-cohen/todo-fe:latest --target testing .'
            }
        }
        stage('Delivery') {
            steps {
                echo 'Delivery step'
                sh 'DOCKER_BUILDKIT=1 docker build -t tehilla-cohen/todo-fe:latest --target delivery .'
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
                sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                sh 'docker push tehillacohen/todo-fe:latest'
            }
        }
    }
}
