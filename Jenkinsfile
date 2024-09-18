pipeline {
    agent any
    tools {
        nodejs "NodeJS"  // This should match the name you configured in Global Tool Configuration
    }
    stages {
        stage("Build") {
            steps {
                // Run npm commands without sudo, as Node.js is now properly configured
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
