pipeline {
    agent {label 'slave-1'}
    
    tools {
        maven 'maven3'
        jdk 'jdk17'
    }

    stages {     
        stage('Compile') {
            steps {
               sh "mvn compile"
            }
        }
        
        stage('Test') {
            steps {
                sh "mvn test"
            }
        }
        
        stage('Build') {
            steps {
                sh "mvn package"
            }
        }

        stage('Trivy fs scan') {
            steps {
                sh "trivy fs --format  table  -o trivy-fs-report.html ."
            }
        }
    }
}
