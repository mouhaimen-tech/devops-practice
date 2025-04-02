pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/mouhaimen-tech/devops-practice.git', branch: 'main'
            }
        }

        stage('Build Backend') {
            steps {
                 dir('/home/codespace/.jenkins/workspace/Java21-Pipeline/devops-practice/spring-boot-server') {
                    sh 'mvn clean package'
                }
            }
        }

        stage('Build Frontend') {
            steps {
                dir('angular-17-client') {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }

        stage('Deploy') {
            steps {
                sh 'ansible-playbook -i inventory.yml deploy.yml'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
