pipeline {
    agent any

    tools {
        maven "maven"
    }

    stages {
        stage('checkout') {
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/socram125/simple-java-maven-app.git']]])
            }
        }
        stage('Build') {
            steps {

                sh "mvn -Dmaven.test.failure.ignore=true clean package"

            }
        } 

        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        
        stage('sonarQube') {
            steps {
                echo 'Aqui va la parte de sonarQube'
            }
        }
        
        stage('email') {
            steps {
                mail bcc: '', body: 'esto es una prueba', cc: '', from: '', replyTo: '', subject: 'jenkins', to: 'soc_126@outlook.com'
                echo 'Aqui va la parte del email'
            }
        }
        
    }
}