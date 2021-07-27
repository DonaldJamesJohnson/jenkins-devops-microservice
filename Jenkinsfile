pipeline {
	//agent { docker { image 'maven:3.8.1'} }
    agent any

    environment {
        PATH = "$PATH"
    }

    stages {
        stage ('Checkout') {
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
        stage ('Compile') {
            steps {
                sh "mvn clean compile"
            }
        }
        stage ('Test') {
            steps {
                sh "mvn test"
            }
        }
        stage ('Integration Test') {
            steps {
                sh "mvn failsafe:integration-test failsafe:verify"
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