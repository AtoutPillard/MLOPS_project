pipeline {
    agent any
    environment {
        BRANCH_NAME = "${GIT_BRANCH.split("/")[1]}"
    }
    stages {
        stage('Building and unit testing'){
            steps{
                echo 'Pulling...' + env.BRANCH_NAME
            }
        }

    }
}
