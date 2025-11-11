pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Ganesh1789/awsprac.git',
                    credentialsId: 'abc8ea96-58cb-45c5-b74f-5a12afd9811b'
            }
        }
        stage('Build') {
            steps {
                sh 'mkdir -p build'
                sh 'javac -d build Hello.java'
            }
        }
        stage('Run') {
            steps {
                sh 'java -cp build Hello'
            }
        }
        stage('Deploy') {
            steps {
                sh 'sudo rm -rf /var/www/html/*'
                sh 'sudo cp -r build/* /var/www/html/'
            }
        }
    }
    post {
        success {
            echo '✅ Build and Deployment Completed Successfully!'
        }
        failure {
            echo '❌ Build Failed — Please Check Console Logs.'
        }
    }
}
