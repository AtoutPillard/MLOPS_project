pipeline {
    agent any

    stages {
        stage('Building and unit testing'){
            when { branch 'feature/*' }

            steps{
                script {
                    def branchName = env.BRANCH_NAME.replace('feature/', '')
                    bat "git checkout ${branchName}"
                    dir('backend_rating') {
                        bat 'pip install -r requirements.txt'
                        bat 'python -m unittest'
                    }
                }
            }
        }
    }
}