pipeline {
    agent {label 'JDK8-Node'}
    triggers {pollSCM ('* * * * *')}
    parameters { choice(name: 'MAVEN_GOAL', choices: ['package', 'test', 'install'], description: 'Maven goals') }
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
}