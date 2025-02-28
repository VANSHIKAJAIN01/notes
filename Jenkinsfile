pipeline {
    agent { label 'dev-server' }

    stages {
        stage("Code clone") {
            steps {
                sh "whoami"
                git branch: 'main', url: 'https://github.com/VANSHIKAJAIN01/django-notes-app.git'
            }
        }
        stage("Code Build") {
            steps {
                sh "docker build -t notes-app:latest ."
            }
        }
        stage("Push to DockerHub") {
            steps {
                withDockerRegistry([credentialsId: 'dockerHubCreds', url: '']) {
                    sh "docker tag notes-app:latest your-dockerhub-username/notes-app:latest"
                    sh "docker push your-dockerhub-username/notes-app:latest"
                }
            }
        }
        stage("Deploy") {
            steps {
                sh "echo Deploying the application..."
                // Add your deployment script here
            }
        }
    }
}
