pipeline {
    agent any

    tools {
        nodejs 'nodejs-20'
    }


    stages {

        stage('Checkout Source Code') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Angular Application') {
            steps {
                sh 'ng build --configuration production'
            }
        }

        stage('Deploy to Nginx') {
            steps {
                sh '''
                sudo rm -rf /var/www/html/angular-app/*
                sudo cp -r dist/tour-of-heroes/* /var/www/html/angular-app/
                '''
            }
        }
    }

    post {
        success {
            echo 'Angular application built and deployed successfully using Jenkins and Nginx'
        }
    }
}