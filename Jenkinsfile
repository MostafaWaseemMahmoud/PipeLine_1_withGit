pipeline {
    agent any

    tools {
        nodejs 'NodeJS_20'
    }

    environment {
        DOCKER_IMAGE = 'mostafawaseem/social-media-app'
        DOCKER_TAG = 'latest'
        DOCKER_USERNAME = 'mostafa-waseem' // استبدل باسم المستخدم الخاص بك في Docker Hub
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Cloning the repository...'
                git branch: 'main', 
                    url: 'https://github.com/MostafaWaseemMahmoud/Socail-Media-Application-F-End.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...' // أضف أوامر لاختبار الكود هنا إذا كانت لديك اختبارات
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t $DOCKER_IMAGE:$DOCKER_TAG .'
            }
        }

        stage('Push Docker Image to Repository') {
            steps {
                echo 'Pushing Docker image to the Docker registry...'
                withCredentials([string(credentialsId: 'docker-hub-credentials', variable: 'DOCKER_PASSWORD')]) {
                    sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin'
                    sh 'docker push $DOCKER_IMAGE:$DOCKER_TAG'
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying the Docker container to production...'
                // هنا يمكن استخدام Docker Compose أو kubectl (Kubernetes) لتشغيل الحاويات في بيئة الإنتاج
                sh 'docker stop social-media-app || true && docker rm social-media-app || true'
                sh 'docker run -d -p 80:3000 --name social-media-app $DOCKER_IMAGE:$DOCKER_TAG'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed! Please check the logs.'
        }
    }
}
