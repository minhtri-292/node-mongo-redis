pipeline {
    agent any
    stages {
        stage('build image') {
            steps {
                checkout scmGit(branches: [[name: '*/dev']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/minhtri-292/node-mongo-redis.git']])
                sh 'docker build -t ntminh/node-mongo-redis:v1 .'
                sh 'docker images'
            }
        }
        stage('push image') {
            steps {
                // This step should not normally be used in your script. Consult the inline help for details.
                withDockerRegistry(credentialsId: 'docker-hub', url: 'https://index.docker.io/v1/') {
                    sh 'docker push ntminh/node-mongo-redis:v1'
                }
            }
        }
    }
}