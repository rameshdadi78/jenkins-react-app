pipeline {
     agent
     stages {
          environment {
                         CI = "true"
                       }
        stage("Build") {
            steps {
                sh "sudo npm install"
                sh "sudo npm run build"
            }
        }
         stage('Test') {
            steps {
                 sh './jenkins/scripts/test.sh'
                  }
               }
        stage("Deploy") {
            steps {
                //sh "sudo rm -rf /var/www/jenkins-react-app"
                sh "sudo cp -r ${WORKSPACE}/build/ /var/www/jenkins-react-app/"
            }
        }
    }
}
