pipeline {
    agent any

    stages {
        stage('Pre-build stg') {
            steps {
                sh 'DOCKER_BUILDKIT=1 docker build -t tehilla:latest --target pre-build .'
            }
        }
        stage('Build') {
            steps {
                sh 'DOCKER_BUILDKIT=1 docker build -t tehilla:latest --target build .'
            }
        }
        stage('Test') {
            steps {
                sh 'DOCKER_BUILDKIT=1 docker build -t tehilla:latest --target test .'
            }
        }
        stage('Security') {
            steps {
                sh 'DOCKER_BUILDKIT=1 docker build -t tehilla:latest --target security .'
            }
        }
        stage('back-end') {
            steps {
                sh 'DOCKER_BUILDKIT=1 docker build -t tehilla:latest --target back-end .'
            }
        }
        stage('front-end') {
            steps {
                sh 'DOCKER_BUILDKIT=1 docker build -t tehilla:latest --target front-end .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'DOCKER_BUILDKIT=1 docker build -t tehilla:latest --target deploy .'
            }    
        }
        stage('Post') {
            steps {
                sh 'DOCKER_BUILDKIT=1 docker build -t tehilla:latest --target post .'
            }
        }                
    }
}
