pipeline {
    agent {label 'JDK8-Node'}
    stages {
        stage ('vcs'){
            steps {
            git url: 'https://github.com/moezharuni/game-of-life.git',
            branch: 'master'
            }
        }   
    }
}