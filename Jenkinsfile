pipeline{
    agent any
    tools {
        node js "NodeJs"
    }
    stages {
        stage("checkout") {
            steps {
                checkout scm
            }
        }
        stage("installed package") {
            steps {
                bat "npm ci"
            }
        }
        stage("build") {
            steps {
                bat "npx ng build --configuration production"
            }
        }
        stage("deployment") {
            steps {
                bat "del /q /s c:\\inetpub\\wwwroot\\anugularnew\\*"
                bat "xcopy /E /Y /I dist\\AngularJenkin\\browser\\* c:\\inetpub\\\wwwroot\\angularnew\\"
            }
        }    
    }
    post {
        success {
            echo "success"
        }
        failure {
            echo "build"
        }
    }
}