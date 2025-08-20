pipeline {
    agent any

    tools {
        maven 'Maven 3' // Make sure "Maven 3" is configured in Jenkins global tools
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Savitha-savi1/simple-maven-project-with-war', branch: 'main'
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

        stage('Deploy') {
            steps {
                sh 'cp target/*.war /opt/tomcat/webapps/'
            }
        }
    }
}
