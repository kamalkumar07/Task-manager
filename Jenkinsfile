pipeline {
    agent any

    tools {
        maven 'Maven'
        jdk 'JDK17'
    }

    stages {

        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/kamalkumar07/Task-manager.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo 'No tests available, skipping...'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t task-manager .'
            }
        }

        stage('Run Docker') {
            steps {
                bat 'docker stop task-manager || exit 0'
                bat 'docker rm task-manager || exit 0'
                bat 'docker run -d -p 8080:8080 --name task-manager task-manager'
            }
        }

    }
}