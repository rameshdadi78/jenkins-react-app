pipeline {
    agent any
    tools {
        nodejs 'NodeJS'  // Use the exact name configured in Global Tool Configuration
    }
    stages {
        stage("Build") {
            steps {
                sh "export NODE_OPTIONS=--openssl-legacy-provider"
                sh "npm install"
                sh "npm run build"
            }
        }
        stage("Deploy") {
            steps {
                sh "sudo rm -rf /var/www/jenkins-react-app"
                sh "sudo cp -r ${WORKSPACE}/build/* /var/www/jenkins-react-app/"
                sh "sudo chown -R www-data:www-data /var/www/jenkins-react-app"
            }
        }
    }
    post {
        success {
            echo 'Deployment Successful!'
        }
        failure {
            echo 'Deployment Failed.'
        }
    }
}
