pipeline {
    agent any

    stages {
        stage('Cloning Game of Life Source code') {
            steps {
                echo "Game of Life closing"
                git 'https://github.com/wakaleo/game-of-life.git'
            }
        }
        stage('Building artifact .war from soruce code ') {
            steps {
                echo "Building Now maven Artifact"
                sh "mvn clean install"
            }
        }
        stage('Deploying .war Artifact on Apache Server') {
            steps {
                echo "Deploying .war Artifact on Apache Server"
                deploy adapters: [tomcat9(credentialsId: 'TomcatLogins', path: '', url: 'http://13.234.202.116:8080/')], contextPath: 'Devops', onFailure: false, war: '**/*.war'
            }
        }
        /*stage('Deleting .war file from Apache Server') {
            steps {
                echo "Deleting .war file from Apache Server"
                sh 'sudo rm -r /home/ec2-user/tomcat/apache-tomcat-10.0.22/webapps/Devops.war'
            }
        } */    
    }
}
