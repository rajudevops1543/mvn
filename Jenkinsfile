pipeline {
    agent any


    stages {
        stage('Start') {
            steps {
                bat "echo ************************Start************************"
            }
        }
        stage('github') {
            steps {
                // Get some code from a GitHub repository to Build
                checkout scmGit(branches: [[name: '*/mayankmvn']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/rajudevops1543/mvn.git']])
            }
        }
        stage('maven') {
            steps {
                // Run Maven on a Unix agent.
                bat "mvn -f javaapp/pom.xml clean package"

                // To run Maven on a Windows agent, use
                // bat "/opt/apache-maven/bin/mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        stage('tomcat') {
            steps {
                //withCredentials([usernamePassword(credentialsId: 'hash', usernameVariable: 'USER_CREDENTIALS_USR', passwordVariable: 'USER_CREDENTIALS_PSW')]) {
                    // Run Maven on a Unix agent.
                bat "mvn -f javaapp/pom.xml clean tomcat7:deploy"
                //}
            }
        }
        stage('docker') {
            steps {
                // Run Maven on a Unix agent.
                bat "echo building docker images"

            }
        }
        stage('End') {
            steps {
                bat "echo ************************Start************************"
            }
        }

    }
}

