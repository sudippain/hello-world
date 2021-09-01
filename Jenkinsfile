pipeline {
    agent {
    }
    stages {
        stage('Building our image') {
            steps {
                script {
                    dockerImage = docker.build "dibyo/hello-world:$BUILD_NUMBER"
                }
            }
        }
        stage('Deploy our image') {
            steps {
                script {
                    // Assume the Docker Hub registry by passing an empty string as the first parameter
                    docker.withRegistry('' , 'dockerhub') {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}
