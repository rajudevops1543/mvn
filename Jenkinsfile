pipeline {
    agent any


    stages {
        stage('github') {
            steps {
                // Get some code from a GitHub repository
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/rajudevops1543/mvn.git']])
            }
        }
        stage('maven') {
            steps {
                // Run Maven on a Unix agent.
                bat "mvn -f javaapp/pom.xml clean package"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        stage('tomcat') {
            steps {
                // Run Maven on a Unix agent.
                bat "mvn -f javaapp/pom.xml clean tomcat7:deploy"
            }
        }
        stage('docker') {
            steps {
                // Run Maven on a Unix agent.
                bat "echo building docker images"

            }
        }

    }
}
