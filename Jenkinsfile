#!/usr/bin/env groovy

pipeline {
    agent any
    stages {
        stage('build app') {
            steps {
               script {
                   echo "building the application..."
               }
            }
        }
        stage('build image') {
            steps {
                script {
                    echo "building the docker image..."
                }
            }
        }
        stage('deploy') {
            steps {
                script {
                   echo 'deploying docker image...'
                   withKubeConfig([credentialsId: 'lke-credentials', serverUrl: 'https://20381b9f-6aa5-4e84-9ea4-3322001bfce7.eu-central-1.linodelke.net:443']) {
                       sh 'kubectl create deployment nginx-deployment --image=nginx'
                   }
                }
            }
        }
    }
}
