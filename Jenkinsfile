pipeline {
    agent {label "JDK17-MVN363"}
    stages {
        stage"vcs"{
            steps {
                git url: "https://github.com/moezharuni/game-of-life.git",
                    branch: "declarative"
            }
        }
        stage"build" {
            steps {
                sh: "mvn package"
            }
        }
        stage"postbuildactions" {
            steps {
                junit testResults : "**/surefire-reports/*.xml",
                archive: Archive artifacts "**/target/gameoflife.war"
            }
        }
    }
}