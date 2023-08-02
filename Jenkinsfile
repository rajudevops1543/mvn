pipeline {
    agent any

    stages {
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
        stage('docker') {
            steps {
                // Run Maven on a Unix agent.
                sh "echo building docker images"

            }
        }

    }
}
