pipeline {
    agent any

    tools {
        // Define the Maven tool using its name
        maven 'M2_HOME' // Make sure 'Maven' matches the tool configuration in Jenkins
    }

    stages {
        stage('Git Checkout') {
            steps {
                // Corrected 'Git checkout' to 'git'
                git branch: 'main', url: 'https://github.com/adedokunk/Petclinic.git'
            }
        }

        stage('Maven Compile') {
            steps {
                // Corrected 'Maven compile' to 'sh'
                sh 'mvn compile'
            }
        }

        stage('Maven Package') {
            steps {
                // Corrected 'Maven package' to 'sh'
                sh 'mvn package'
            }
        }
        
        stage('Deploy to TomcatServer') {
            steps {
                // Corrected 'Maven package' to 'sh'
        }        sh 'sudo cp target/*.war /opt/apache-tomcat-9.0.65/webapps'
        }
    }
}
