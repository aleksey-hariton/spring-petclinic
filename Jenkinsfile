pipeline {
    agent {
        kubernetes {
            defaultContainer 'maven'
            yaml """
                kind: Pod
                spec:
                  containers:
                  - name: maven
                    image: maven:alpine
                    command: ["cat"]
                    tty: true
            """
        }
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        // stage('Deploy') {
        //     steps {
        //     }
        // }
    }
    // post {
    //     always {
    //         // Clean up steps here
    //     }
    //     success {
    //         // Success notification or steps here
    //     }
    //     failure {
    //         // Failure notification or steps here
    //     }
    // }
}
