pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                // Install dependencies and build the React app without sudo
                sh "npm install"
                sh "npm run build"
            }
        }
        stage("Deploy") {
            steps {
                // Clean the old build directory
                sh "sudo rm -rf /var/www/jenkins-react-app"
                
                // Copy the new build to the target directory
                sh "sudo cp -r ${WORKSPACE}/build/* /var/www/jenkins-react-app/"
                
                // Set proper ownership on the deployed files (optional)
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
