pipeline {
    agent any

    stages {
        stage('pull code') {
            steps {
               checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'b420ecc5-41b4-4510-8596-681e324888c7', url: 'git@github.com:ding1002/jenkinsDemo.git']]])
            }
        }
         stage('build project') {
            steps {
                sh 'mvn clean package'
            }
        }
         stage('publish project') {
            steps {
                   deploy adapters: [tomcat8(credentialsId: 'd4500dd2-db55-401b-8c90-98cd27eff89d', path: '', url: 'http://192.168.80.132:8080/')], contextPath: null, war: 'target/*.war'
            }
        }
    }
}
