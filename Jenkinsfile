pipeline {
    agent any
    stages {
        stage('compile') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
}
