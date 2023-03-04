pipeline {
    agent any
    triggers {
        pollSCM 'H/* * * * *'
    }
    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "MAVEN"
        jdk "JDK"
    }
    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git credentialsId: 'd6974fb2-6411-4d16-96ae-8e113e3af13e', url: 'https://github.com/Colin-Moore/comp367-lab2.git'
                bat "mvn clean compile"
            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    echo "Build complete"
                }
            }
        }
    }
}
