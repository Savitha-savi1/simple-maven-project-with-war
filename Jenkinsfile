pipeline {
    agent any
    tools { maven 'Maven 3' }

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
        stage('Deploy') {
            steps {
                echo 'Deploying WAR to Tomcat...'
                sh '''
                WAR_FILE=$(ls target/*.war | head -n 1)
                sudo cp $WAR_FILE /home/ec2-user/apache-tomcat-9.0.108/webapps/
                sudo systemctl restart tomcat
                '''
            }
        }
    }
    post {
        success { echo 'Deployment Successful! 🎉' }
        failure { echo 'Build Failed ❌ Check console logs.' }
    }
}
