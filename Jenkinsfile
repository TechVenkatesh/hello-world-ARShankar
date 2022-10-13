pipeline {
    agent {label 'test'}
    options {
        buildDiscarder (logRotator(numToKeepStr: '1'))
        timeout (unit: 'MINUTES', time: 5)
    }
    stages {
        stage('checkout scm') {
            steps {
                git branch: 'master', credentialsId:'', url: 'https://github.com/jay19888/hello-world-1.git'
            }
        }
        stage ('code analysis'){
            steps {
                withsonarQubeEnv('sonarqube'){
                    sh "mvn clean verify sonar:sonar -Dsonar.projectKey=devops_project"
                }

            }
        }
    }
}
