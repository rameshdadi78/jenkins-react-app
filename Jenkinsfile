pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                bat "npm install"
                bat "npm run build"
            }
        }
        stage("Deploy") {
            steps {
                bat "rmdir /s /q C:\\var\\www\\jenkins-react-app"
                bat "xcopy /e /i /y ${WORKSPACE}\\build C:\\var\\www\\jenkins-react-app"
            }
        }
    }
}
