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
            environment {
                sh 'export PATH = "/usr/lib/jvm//java-1.8.0-openjdk-amd64/bin:$PATH" && mvn package '
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