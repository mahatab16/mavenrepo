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
                  branch 'master'
            } 
            steps {
                  script {
                         currentBuild.displayName = "${REVISION}"
                 }
        
                sh 'mvn deploy scm:tag -Drevision=${REVISION}'
           }
       }
    }
}
