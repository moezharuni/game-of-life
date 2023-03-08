pipeline {
    agent {label 'JDK8-Node'}
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
                sh 'mvn package'
            }
        }
        stage ('archive') {
            steps {
                archiveArtifacts artifacts: '**/surefire-reports/*.xml',
                junit '**/gameoflife.war'
            }
        }
    }
}