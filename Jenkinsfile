pipeline {
    agent any

    stages {
        stage ('checkout') {
            steps {
                git credentialsId: 'mooneshbmsit-git', url: 'https://github.com/mooneshbmsit/shared-hello-world.git', branch: 'main'
            }
        }
        stage ('Build image') {
            steps {
                sh 'docker build -t moon:l1 .'
            }
        }
    }
}
