pipeline {
    agent any

    tools {
        // Define the Maven tool using its name
        maven 'M2_HOME' // Make sure 'M2_HOME' matches the tool configuration in Jenkins
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
        
        stage('Deploy to TomcatServer') {
            steps {
                sh 'sudo cp target/*.war /opt/apache-tomcat-9.0.65/webapps'
            }
        }
    }
}
