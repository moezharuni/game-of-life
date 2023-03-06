pipeline {
    agent {label 'JDK17_MVN363'}
    stages {
        stage ('vcs') {
            steps {
                git url: 'https://github.com/moezharuni/game-of-life.git',
                branch: declarative1
            }
        }
    }
}