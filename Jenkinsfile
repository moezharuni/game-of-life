pipeline {
    agent {label 'JDK17_MVN363'}
    triggers { pollSCM ('* * * * *')}
    stages {
        stage ('vcs') {
            steps {
                git url: 'https://github.com/moezharuni/game-of-life.git',
                branch: 'declarative1'
            }
        }
        stage ('build') {
            steps {
                 sh 'export PATH="/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH" && mvn package'
            }
        }
        stage ('tests'){
            steps{
                junit testResults: '**/surefire-reports/*.xml'
            }
        }
        stage ('archive') {
            steps {
                archiveArtifacts artifacts: '**/target/gameoflife.war'
            }
        }
    }
}