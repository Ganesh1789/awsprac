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
                echo '⚙️ Compiling Java Project...'
                sh '''
                mkdir -p build
                javac -d build Hello.java
                '''
            }
        }

        stage('Run') {
            steps {
                echo '▶️ Running Java Program...'
                sh 'java -cp build Hello'
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Deploying to Web Directory...'
                sh '''
                # Ensure target directory exists
                mkdir -p /var/www/html
                # Remove old files and copy new ones
                rm -rf /var/www/html/*
                cp -r build/* /var/www/html/
                echo "✅ Files deployed successfully to /var/www/html"
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Build, Run, and Deployment Completed Successfully on Jenkins!'
        }
        failure {
            echo '❌ Build Failed — Please Check Console Logs.'
        }
    }
}
