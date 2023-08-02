pipeline {
    agent any

    environment {
        USER_CREDENTIALS = credentials('3c1dd8a3-7842-4136-bf01-7b719a140c05')
    }
    stages {
        stage('Run') {
            steps {
                sh "echo $USER_CREDENTIALS_USR"
                sh "echo $USER_CREDENTIALS_PSW"
            }
        }
        stage('github') {
            steps {
                // Get some code from a GitHub repository to Build
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/rajudevops1543/mvn.git']])
            }
        }
        stage('maven') {
            steps {
                // Run Maven on a Unix agent.
                sh "/opt/apache-maven/bin/mvn -f javaapp/pom.xml clean package"

                // To run Maven on a Windows agent, use
                // bat "/opt/apache-maven/bin/mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        stage('tomcat') {
            steps {
                //withCredentials([usernamePassword(credentialsId: 'hash', usernameVariable: 'USER_CREDENTIALS_USR', passwordVariable: 'USER_CREDENTIALS_PSW')]) {
                    // Run Maven on a Unix agent.
                sh "/opt/apache-maven/bin/mvn -f javaapp/pom.xml clean tomcat7:deploy"
                //}
            }
        }
        stage('docker') {
            steps {
                // Run Maven on a Unix agent.
                sh "echo building docker images"

            }
        }

    }
}

