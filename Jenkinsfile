pipeline {
    agent any
    stages {
        stage('checkout'){
            steps{
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '47abb2dd-15e2-4c1d-9348-37cd39fa026d', url: 'https://github.com/n1kkhub/raviLogin.git']])
            }
        }    
        stage('validate'){
            steps{
                sh 'mvn validate'
            }
        }    
        stage('compile'){
            steps {
                sh 'mvn compile'
            }
        }
        stage('test'){
            steps{
                sh 'mvn test'
            }
        }
        stage('package'){
            steps{
                sh 'mvn package'
            }
        }
        stage('deploy to tomcat'){
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://3.93.62.119:8080')], contextPath: 'mybatch', war: '**/*.war'
            }
        }    
    }
}
