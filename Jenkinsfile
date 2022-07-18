pipeline {
    agent any

    tools {
        jdk 'JAVA_1.8'
        maven 'MAVEN_3.5.2'
        git 'Default'
    }

      stages {
        stage('checkout') {
            steps {
                git branch:'main', credentialsId: 'github-private-key', poll: false, url: 'https://github.com/AnmolChapagain/eficens-project1.git'
            }
        }

    stages {
        stage('Build') {
            steps {
                sh 'mnv -B -DskipTests clean '
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post{
                always {
                    junit 'server/target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
}
 
