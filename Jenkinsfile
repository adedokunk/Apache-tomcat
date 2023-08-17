pipeline {
    agent any

    tools {
        maven 'M2_HOME'
    }

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/adedokunk/Petclinic.git'
            }
        }

        stage('Maven Compile') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('Maven Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Static Code Analysis') {
            environment {
                SONAR_URL = "http://44.211.125.22:9000/"
            }
            steps {
                withCredentials([string(credentialsId: 'sonar', variable: 'SONAR_AUTH_TOKEN')]) {
                    sh '''
                        cd /Apache-tomcat.git
                        mvn sonar:sonar -Dsonar.login=$SONAR_AUTH_TOKEN -Dsonar.host.url=${SONAR_URL}
                    '''
                }
            }
        }

        stage('Deploy to TomcatServer') {
            steps {
                sh 'sudo cp -r /var/lib/jenkins/workspace/tomact-job/target/petclinic.war * /opt/apache-tomcat-9.0.65/webapps'
            }
        }
    }
}
