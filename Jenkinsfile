pipeline {
    agent any

    // Use the Maven tool you configured in Jenkins (Global Tool Configuration)
    tools {
        maven 'M3'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/shyamsut/hello-java-maven.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn -B clean package'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'BUILD SUCCESS'
        }
        failure {
            echo 'BUILD FAILED'
        }
    }
}
