pipeline {
    agent {label 'JDK17_MVN363'}
    triggers { cron ('* * * * *')}
    stages {
        stage ('vcs') {
            steps {
                git url: 'https://github.com/moezharuni/game-of-life.git',
                branch: 'declarative1'
            }
        }
        stage ('build') {
            steps {
                 sh 'mvn package'
            }
        }
    }
}