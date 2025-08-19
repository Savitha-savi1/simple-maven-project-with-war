pipeline {
    agent any

    tools {
        maven 'Maven 3' // Ensure Maven 3 is configured in Jenkins (Global Tool Configuration)
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Savitha-savi1/simple-maven-project-with-war.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying WAR to Tomcat...'
                sh '''
                WAR_FILE=$(ls target/*.war | head -n 1)
                sudo cp $WAR_FILE /var/lib/tomcat/webapps/
                '''
            }
        }
    }

    post {
        success { 
            echo 'Deployment Successful! 🎉' 
        }
        failure { 
            echo 'Build Failed ❌' 
        }
    }
}
