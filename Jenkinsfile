pipeline {
    agent any
    
    stages {
        stage('Cloning from git') {
            steps {
               git branch: 'main', url: 'https://github.com/Afraz33/MLOPS_Week4.git'
            }
        }

        stage('Installation of dependencies') {
            steps {
                sh 'pip3 install -r requirement.txt'
                echo 'Dependencies successfully installed!'
            }
        }

        stage('Test') {
            steps {
                sh 'python test.py'
                echo 'Tests passed!'
            }
        }

        stage('Deploy') {
            steps {
                script {
                     
                     env.BRANCH_NAME = scm.branches[0].name
                     echo "Branch name: ${env.BRANCH_NAME}"
                    if (env.BRANCH_NAME == 'main') {
                        echo 'Deploying to production...'
                    } else {
                        echo 'Deploying to development server...'
                    }
                }
            }
        }
    }
}