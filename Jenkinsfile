pipeline {
    agent {label 'JDK17_MVN363'}
    triggers { pollSCM ('* * * * *')}
    parameters {
        choice(name: 'MAVEN_GOAL2', choices: ['package', 'install', 'test', 'compile'], description: 'Maven Options')
    }
    stages {
        stage ('vcs') {
            steps {
                git url: 'https://github.com/moezharuni/game-of-life.git',
                branch: 'declarative1'
            }
        }
        stage ('build') {
            steps {
                 sh "export PATH='/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH' && mvn ${params.MAVEN_GOAL2}"
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
        post {
            success {
                mail to:"mharuni@gmail.com", subject:"Build1", body: "PASSED !!!"
        }
        failure {
            mail to:"mharuni@gmail.com", subject:"FAILURE: Build2", body: "FAILED !!!"
        }

        }
    
    
}