pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'git 'https://github.com/Ganesh1789/awsprac.git'
'
            }
        }
        stage('Build') {
            steps {
                sh 'mkdir -p build'
                sh 'javac -d build src/Hello.java'
            }
        }
        stage('Run') {
            steps {
                sh 'java -cp build Hello'
            }
        }
    }
}
