pipeline {
    agent {label "JDK17-MVN363"}
    tools {
        jdk 'JDK-8' 
    }
    stages {
        stage("vcs"){
            steps {
                git url: "https://github.com/moezharuni/game-of-life.git",
                    branch: "declarative"
            }
        }
        stage("build") {
            steps {
                sh "mvn package"
            }
        }
        stage("postbuildactions") {
            steps {
                junit testResults : "**/surefire-reports/*.xml",
                archiveArtifacts artifacts: '**/target/*.jar'
            }
        }
    }
}