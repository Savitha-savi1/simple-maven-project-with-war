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
                cp $WAR_FILE /home/ec2-user/apache-tomcat-9.0.108/webapps/
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
