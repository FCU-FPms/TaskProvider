pipeline {
    agent none
    stages {
        stage('add jdbc to workspace') {
            agent {
                docker {
                    image 'alpine:latest'
                }
            }
            steps {
                sh 'echo "pwd = ${pwd}"'
                sh 'echo "YAYA"'
                sh "cp ../../franky-mysql/jdbc.properties ./src/main/resources/jdbc.properties"
            }
        }

        stage('Build') {
            agent {
                docker {
                    image 'maven:3-alpine'
                    args '-v $HOME/.m2:/root/.m2'
                }
            }
            steps {
                sh 'mvn --version'
                sh "mvn -B -DskipTests=true clean package"
            }
        }
    }
}
