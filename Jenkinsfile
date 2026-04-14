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
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t task-manager .'
            }
        }

        stage('Run Docker') {
            steps {
                sh 'docker stop task-manager || true'
                sh 'docker rm task-manager || true'
                sh 'docker run -d -p 8080:8080 --name task-manager task-manager'
            }
        }
    }
}