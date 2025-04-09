pipeline {
    agent any
        tools {
        maven 'Maven' // Optional: remove if not using Maven
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/arulmurugan001/definesteps.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully file created by Arul murugan.'
        }
        failure {
            echo 'Build failed!'
        }
        always {
            junit '**/target/surefire-reports/*.xml'
            archiveArtifacts '**/target/*.jar'
        }
    }
}