pipeline {
    agent any
    environment {
    REVISION = "0.0.${env.BUILD_ID}"
    }
    parameters {
        string(name: 'deploy-env', defaultValue: 'SNAPSHOT', description: 'Where you want to deploy?')
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
                  script {
                         currentBuild.displayName = "${REVISION}"
                 }
        
                sh 'mvn deploy'
           }
       }
    }
}
