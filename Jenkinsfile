pipeline {
    agent any

    tools {
        nodejs 'NodeJS_20' // Ensure this matches the Node.js toolchain in Jenkins
    }

    environment {
        PATH = "/usr/bin:/usr/local/bin:${env.PATH}" // Update to match your environment
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
                echo "Install Dependencies"
                sh '''
                    echo "Node Version:"
                    node -v
                    echo "NPM Version:"
                    npm -v
                    npm install
                '''
            }
        }

        stage('Testing The Code') {
            steps {
                echo "Test Code"
                sh 'echo "Running Tests"'
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
