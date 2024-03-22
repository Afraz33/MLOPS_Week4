pipeline {
    agent any

    stages {
        stage('Cloning the repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Afraz33/MLOPS_Week4.git'
            }
        }

        stage('Installation of dependencies') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Execution of test.py') {
            steps {
                sh 'pytest test.py'
            }
        }

        stage('Deploying step') {
            steps {
                script {
                    def branchName = sh(script: 'git rev-parse --abbrev-ref HEAD', returnStdout: true).trim()
                    if (branchName == 'main') {
                        echo 'Deploying to production'
                    } else {
                        echo 'Deploying to UAT'
                    }
                }
            }
        }
    }
}