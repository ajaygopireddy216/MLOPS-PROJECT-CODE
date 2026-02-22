@Library('jenkins-shared') _

pipeline {
    agent any
    environment {
        DOCKER_REPO = "ajaygopireddy216/jenkins-shared-mlops-project"
    }
    stages {
        stage('Checkout') {
            steps {
                gitCheckout('https://github.com/ajaygopireddy216/MLOPS-PROJECT-CODE.git','*/main','github-token')

            }
        }

        stage('Build & Push Image') {
            steps {
                dockerBuildAndPush(DOCKER_REPO,'dockerhub-token')
            }
        }

        stage('Install Kubectl') {
            steps {
               installKubectl()
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                k8sDeploy('kubeconfig')
            }
        }
    }
}
