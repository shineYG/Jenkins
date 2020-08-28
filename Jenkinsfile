pipeline {
    agent any

    stages {
        stage('pull code') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'e479d602-d8ef-49f4-8bf1-2ab81e20caf0', url: 'https://github.com/shineYG/Jenkins.git']]])
            }
        }
         stage('build project') {
            steps {
                sh 'mvn clean package'
            }
        }
         stage('publish project') {
            steps {
                deploy adapters: [tomcat8(credentialsId: '20684a62-afd3-456c-8580-2794b17fa71e', path: '', url: 'http://192.168.224.3:8080')], contextPath: null, war: 'target/*.war'
            }
        }
    }
}
