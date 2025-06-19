pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building on branch: ${env.BRANCH_NAME}"
                sh 'echo "Build done" > build.txt'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests"
                sh 'free -h'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'main') {
                        echo "Deploying to production environment!"
                        sh 'df -h'
                    } else {
                        echo "Skipping deployment on ${env.BRANCH_NAME} branch"
                    }
                }
            }
        }
    }

    post {
        success {
            echo "✅ Build for ${env.BRANCH_NAME} completed successfully"
        }
        failure {
            echo "❌ Build for ${env.BRANCH_NAME} failed"
        }
    }
}

