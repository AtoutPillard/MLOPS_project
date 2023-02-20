pipeline {
    agent any

    stages {
        stage('Building and unit testing'){
            steps{
                script {
                    def branchName = env.GIT_BRANCH
                    bat "git checkout ${branchName}"
                    dir('backend_rating') {
                        bat 'pip install -r requirements.txt'
                        bat 'python -m unittest'
                    }
                    bat "git checkout dev"
                    bat "git merge ${branchName}"
                    bat "git push origin dev"
                }
            }
        }

    }
}
