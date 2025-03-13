pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM',
                          branches: [[name: '*/main']],
                          userRemoteConfigs: [[url: 'https://github.com/kolipakulaHARSHA/CC_LAB8.git']]])
            } // <- This was missing!  VERY IMPORTANT.
        } // <- and this one

        stage('Build') {
            steps {
                sh 'g++ -o PES1UG22CS288-1 main.cpp' // Compiles C++ file
            }
        }

        stage('Test') {
            steps {
                sh './PES1UG22CS288-1' // Runs the compiled file
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying the application..."
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed' // Post action in case of failure
        }
    }
}
