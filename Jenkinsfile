pipeline {
    agent any
    environment {
    REVISION = "0.0.${env.BUILD_ID}"
    }
    stages {
        stage('compile') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package -Dv=${BUILD_NUMBER}'
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
