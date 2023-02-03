pipeline {
    agent { label 'jdk11' }
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('vcs') {
            steps {
                git branch: 'develop', url: 'https://github.com/GitPracticeRepositorys/nopCommerce.git'
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('docker image build') {
            steps {
                sh 'docker build -t shivakrishna99/nopCommerce .'
            }
        }
        stage('push image to registry') {
            steps {
                sh 'docker push shivakrishna99/nopCommerce'
            }
        }
    }
}
