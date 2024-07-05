pipeline {
    agent any

    tools {
        go 'go1.14'
    }

    stages {
         stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/govindh369/micro-product-go.git'
            }
        }
        stage("unit-test") {
            steps {
                echo 'UNIT TEST EXECUTION STARTED'
                sh 'make unit-tests'
            }
        }
        stage("functional-test") {
            steps {
                echo 'FUNCTIONAL TEST EXECUTION STARTED'
                sh 'make functional-tests'
            }
        }
        stage("build") {
            steps {
                echo 'BUILD EXECUTION STARTED'
                sh 'go version'
                sh 'go get ./...'
                sh 'go build -o build/output.exe ./main.go' // Adjust the output path and main file as needed
            }
        }
        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'build/output.exe', allowEmptyArchive: true
            }
        }
    }
}
