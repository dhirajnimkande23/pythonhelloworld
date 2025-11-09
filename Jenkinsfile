 pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/dhirajnimkande23/pythonhelloworld.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build('python-hello-world')
                    echo 'Docker Image build successfull'
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    dockerImage.run()
                    echo 'Container created'
                }
            }
        }
        stage('Push to Docker Hub') {
         steps {
             script {
                 docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-creds') {
                     dockerImage.push()
                     echo 'Docker Hub Pushed to Docker Hub'
             }
         }
        }
     }
}
 }
