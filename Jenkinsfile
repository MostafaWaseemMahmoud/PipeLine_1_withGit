pipeline {
    agent any

    tools {
        nodejs 'NodeJS_20' // Specify your Node.js toolchain name here
    }

    environment {
        DOCKER_IMAGE = 'mostafawaseem/social-media-app'
        DOCKER_TAG = 'latest'
        DOCKER_USERNAME = 'mostafa-waseem' // استبدل باسم المستخدم الخاص بك في Docker Hub
    }

    stages {
        stage('Check Out Code From Rep') {
            steps {
                echo "Getting Repo"
                git branch: 'main', url: "https://github.com/MostafaWaseemMahmoud/FaceBook-React"
            }
        }
        
        stage('Install Dependensies') {
            steps {
                echo "Install Dependensies"
                sh 'npm install'
            }
        }

        stage('Testing The Code') {
            steps {
                echo "Test Code"
                echo "Testing"
            }
        }
    }

    post {
        success {
            echo 'PipeLine succeeded!'
        }
        failure {
            echo 'PipeLine failed!'
        }
        always {
            echo '--> You Reach The End Of The PipeLine <--'
        }
    }
}