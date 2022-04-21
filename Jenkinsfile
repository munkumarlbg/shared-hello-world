pipeline {
    agent any

    environment {
        registry = "mooneshbmsit/my-app"
        registryCredential = 'dockerhub'
        dockerImage = ''
    }

    stages {
        stage ('checkout') {
            steps {
                git credentialsId: 'mooneshbmsit-git', url: 'https://github.com/mooneshbmsit/shared-hello-world.git', branch: 'main'
            }
        }
        stage ('Build image') {
            steps {
                script {
                    dockerImage = docker.build registry
                }
            }
        }
        stage ('Push image') {
            steps {
                script {
                    docker.withRegistry( '', registryCredential ) {
                        dockerImage.push()
                    }
                }
            }
        } 
        stage ('checkout_helm_chart') {
            steps {
                git credentialsId: 'mooneshbmsit-git', url: 'https://github.com/mooneshbmsit/dummy_nginx_helm.git', branch: 'main'
            }
        }
        stage ('Pull nxinx image') {
            steps {
                script {
                    docker.withRegistry( '', registryCredential ) {
                        dokcerImage.pull
                    }
                }
            }
        }
        stage ('Deploy chart') {
            steps {
                script {
                    sh "helm upgrade nginx-server"
                }
            }
        }
    }
}
