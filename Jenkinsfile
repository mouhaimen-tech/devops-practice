pipeline {
    agent any
    environment {
        JAVA_HOME = "/usr/lib/jvm/java-11-openjdk-amd64"
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }
    stages {
        stage('Setup') {
            steps {
                sh 'java -version'
                sh 'echo "Environment ready!"'
            }
        }
        stage('Compile') {
            steps {
                sh 'javac src/HelloWorld.java'
            }
        }
        stage('Run') {
            steps {
                sh 'java -cp src HelloWorld'
            }
        }
        stage('Deploy') {
            steps {
                sh 'ansible-playbook -i hosts deploy.yml'
            }
        }
    }
}
