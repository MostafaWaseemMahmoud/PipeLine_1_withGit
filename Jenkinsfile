pipeline {
    agent any

    tools {
        nodejs 'NodeJS_20' // Specify your Node.js toolchain name here
    }

    environment {
        PATH = "/mnt/c/Program Files/nodejs:PATH" // Add Node.js to PATH
    }

    stages {
        stage('Check Out Code From Rep') {
            steps {
                echo "Getting Repo"
                git branch: 'main', url: "https://github.com/MostafaWaseemMahmoud/Socail-Media-Application-F-End"
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