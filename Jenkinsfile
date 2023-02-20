pipeline {
    agent any
    environment {
        BRANCH_NAME = env.GIT_BRANCH
    }
    stages {
        stage('Building and unit testing'){
            steps{
                bat "git checkout ${BRANCH_NAME}"
                dir('backend_rating') {
                    bat 'pip install -r requirements.txt'
                }
            }
        }
        stage('Push to Develop') {
            
            steps {
                bat "git checkout dev"
                bat "git merge ${BRANCH_NAME}"
                bat "git push origin dev"
                bat "git branch -d ${BRANCH_NAME}"
            }
        }
        stage('User Acceptance') {
            steps {
                input {
                    'Proceed to push to main'
                }
            }
        }
        stage('Pushing to main') {
            steps {
                bat 'git checkout main'
                bat 'git merge dev'
                bat 'git push origin main'
            }
        }
        stage('Pushing to Dockerhub') {
            steps {
                bat 'git checkout main'
                dir('backend_rating') {
                    bat 'docker build -t prediction_api .'
                    bat 'docker run -p 5000:5000 prediction_api'
                }
                bat 'docker-compose up'
            }
        }
    }
}
