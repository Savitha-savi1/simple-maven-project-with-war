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
        # Stop Tomcat
        /opt/tomcat/bin/shutdown.sh

        # Copy WAR
        cp target/simple-war-app-1.0-SNAPSHOT.war /opt/tomcat/webapps/

        # Start Tomcat
        /opt/tomcat/bin/startup.sh
        '''
    }
}

    }
}
