pipeline {
    agent any

    environment {
        AWS_REGION = "ap-south-1"
        ECR_REPO = "420795650215.dkr.ecr.ap-south-1.amazonaws.com/myapp"
        IMAGE_TAG = "${BUILD_NUMBER}"
    }

    stages {

        stage('Clone Code') {
            steps {
                git '<YOUR_GITHUB_URL>'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t myapp:${IMAGE_TAG} .'
            }
        }

        stage('Login ECR') {
            steps {
                sh '''
                aws ecr get-login-password --region $AWS_REGION | \
                docker login --username AWS --password-stdin $ECR_REPO
                '''
            }
        }

        stage('Tag Image') {
            steps {
                sh 'docker tag myapp:${IMAGE_TAG} $ECR_REPO:${IMAGE_TAG}'
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push $ECR_REPO:${IMAGE_TAG}'
            }
        }
    }

    post {
        success {
            sh '''
            aws lambda invoke \
            --function-name myLambdaFunction \
            output.txt
            '''
        }
    }
}
