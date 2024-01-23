pipeline {
    agent { label'JDK_8' }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/raviteja811811/game-of-lifer.git',
                branch: 'try'
            }
        }
        stage ('build') {
            steps {
                sh 'maven build'
            }
        }
        stage ('testing') {
            steps {
                archiveArtifacts artifacts: '**/target/game-of-life.war',
                                     onlyIfSuccessful: true
                junit testResults:'**/surefire-reports/TEST-*.xml'
            }
        }
    }
}