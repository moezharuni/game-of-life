pipeline {
    agent {label 'JDK8-Node'}
    triggers {pollSCM ('* * * * *')}
    parameters { choice(name: 'MAVEN_GOAL', choices: ['package', 'test', 'install', 'compile'], description: 'Maven goals') }
    tools {
        jdk 'JDK-8'
    }
    stages {
        stage ('vcs'){
            steps {
            git url: 'https://github.com/moezharuni/game-of-life.git',
            branch: 'master'
            }
        }
        stage ('build'){
            steps {
                sh "mvn ${params.MAVEN_GOAL}"
            }
        }
        stage ('sonar'){
            steps {
                withSonarQubeEnv('My SonarQube Server'){
                sh 'mvn clean package sonar:sonar -Dsonar.organization=springpetclinic25'
            }}
        }
        stage ('archive') {
            steps {
                archiveArtifacts artifacts: '**/target/*.war'
            }
        }
        stage ('junit') {
            steps {
                junit '**/surefire-reports/*.xml'
            }
        }
    }
    post {
        success {
            mail subject: "Build1 success",
            body: "Build1 success",
            to: "mharuni16@gmail.com",
            from: "qtdevops@gmail.com"
            }
        failure {
            mail subject: "Build1 failed",
            body: "Build1 failed",
            to: "mharuni16@gmail.com",
            from: "qtdevops@gmail.com" 
            }
        }
}