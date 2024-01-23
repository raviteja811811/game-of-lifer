pipeline {
    agent { label'JDK_8' }
    stages {
        stage("vcs") {
            step {
                sh 'https://github.com/raviteja811811/game-of-lifer.git'
            }
        }
        stage ("build") {
            step {
                sh 'maven build'
            }
        }
        stage ("testing") {
            step {
                archiveArtifacts artifacts: '**/target/game-of-life.war',
                                     onlyIfSuccessful: true
                junit testResults:'**/surefire-reports/TEST-*.xml'
            }
        }
    }
}