pipeline {
    agent { label 'JDK_8' }
    triggers { pollSCM ('H/30 * * * *') }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/raviteja811811/game-of-lifer.git',
                    branch: 'try'
            }
        }
        stage('package') {
            tools {
                jdk 'JDK_8'
            }
            steps {
                sh 'mvn package'
            }
        }
        stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                                 onlyIfSuccessful: true
                junit testResults: '**/surefire-reports/TEST-*.xml'
            }
        }
    }
}    