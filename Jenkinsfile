pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    def app = docker.build("your-dockerhub-username/jenkins-php")
                }
            }
        }
        
        stage('Push') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub-credentials') {
                        def app = docker.image("your-dockerhub-username/jenkins-php")
                        app.push("${env.BUILD_NUMBER}")
                        app.push("latest")
                    }
                }
            }
        }
    }
}
