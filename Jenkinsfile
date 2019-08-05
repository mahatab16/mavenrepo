pipeline {
    agent any
    environment {
    REVISION = "0.0.${env.BUILD_ID}"
    }
    parameters {
        string(name: 'environment', defaultValue: 'SNAPSHOT', description: 'The target environment')
        string(name: 'environment', defaultValue: 'RELEASE', description: 'The target environment')
    }
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
        stage('deploy') {
            when {
                  branch 'dev'
            }
            steps {
                echo "${params.environment} World!"
               sh 'mvn deploy'
            }
       }
    }
}
