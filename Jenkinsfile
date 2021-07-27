pipeline {
	//agent { docker { image 'maven:3.8.1'} }
    agent any

    environment {
        PATH = "$PATH"
    }

    stages {
        stage ('Build') {
            steps {
                echo "$PATH"
                sh "mvn --version"
                sh "docker --version"
                echo "Build"
                echo "PATH - $PATH"
                echo "BUILD_NUMBER - $env.BUILD_NUMBER"
                echo "BUILD_ID - $env.BUILD_ID"
                echo "JOB_NAME - $env.JOB_NAME"
                echo "BUILD_TAG - $env.BUILD_TAG"
                echo "BUILD_URL - $env.BUILD_URL"
            }
        }
        stage ('Test') {
            steps {
                echo "Test"
            }
        }
        stage ('Integration Test') {
            steps {
                echo "Integration Test"
            }
        }
    }
    post {
        always {
            echo "Finished Run"
        }
        success {
            echo "Successful Run"
        }
        failure {
            echo "Failed Run"
        }
    }
}