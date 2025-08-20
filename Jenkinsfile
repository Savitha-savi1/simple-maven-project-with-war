pipeline {
    agent any

    tools {
        maven 'Maven 3'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Savitha-savi1/simple-maven-project-with-war', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                // Skip tests while building
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                cp target/*.war /opt/tomcat/webapps/
                /opt/tomcat/bin/shutdown.sh
                /opt/tomcat/bin/startup.sh
                '''
            }
        }
    }
}
