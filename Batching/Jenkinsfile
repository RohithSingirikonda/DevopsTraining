pipeline {
    agent any

    stages {
        stage('SCM Stage') {
            steps {
                echo 'Hello Batch3 Devops Champs'
                git 'https://github.com/wakaleo/game-of-life.git'
            }
        }
        
        stage('Artifact Build stage') {
            steps {
                echo 'buliding with maven tool'
                sh 'mvn clean install'
            }
        }
        
        stage('Deploy to Tomcat stage') {
            steps {
                echo 'deploying to LAB tomcat '
                deploy adapters: [tomcat9(credentialsId: '7a936ec4-bfa5-4450-854a-0dff0c2e8547', path: '', url: 'http://34.227.157.196:8080/')], contextPath: 'batch3', war: '**/*.war'
            }
        }
        
    }
}
