#!groovy
@Library('jenkinslib')

def tools = new org.devops.tools()
  pipeline {
    agent { label "jenkins-slave"}
    options {
        timestamps()
        timeout(time: 1, unit: 'HOURS')
    }
    parameters {
        string(name: 'TYPE',defaultValue: 'init', description: '初始化')
        string(name: 'ENV',defaultValue: 'dev', description: 'dev环境')
    }
    environment{
        type="${params.TYPE}"
        env="${params.ENV}"
    }
    stages {
        stage('init') {
            when { environment name: 'type', value: 'init'}
            steps {
                echo "$env.type"
                script{
                    sh 'helm version'
                }
            }
        }
        stage('build') {
            when { environment name: 'type', value: 'deploy'}
            steps {
                echo "$env.env"
                script{
                    sh 'helm version'
                    tools.PrintMes("this is a jenkinsfile!")
                }
            }
        }
    }
}
