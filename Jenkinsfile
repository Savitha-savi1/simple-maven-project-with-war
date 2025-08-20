pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Savitha-savi1/simple-maven-project-with-war.git'
            }
        }

        stage('Build') {
            steps {
                // Build WAR and skip tests (since none exist)
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying WAR to Tomcat...'
                sh '''
                # Find the WAR file
                WAR_FILE=$(ls target/*.war | head -n 1)
                
                # Copy to Tomcat webapps
                cp $WAR_FILE /home/ec2-user/apache-tomcat-9.0.108/webapps/
                
                # Restart Tomcat safely
                /home/ec2-user/apache-tomcat-9.0.108/bin/shutdown.sh || true
                /home/ec2-user/apache-tomcat-9.0.108/bin/startup.sh
                '''
            }
        }
    }

    post {
        success { echo 'Deployment Successful! 🎉' }
        failure { echo 'Build Failed ❌ Check console logs.' }
    }
}
