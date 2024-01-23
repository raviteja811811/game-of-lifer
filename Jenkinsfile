pipeline {
    agent { label'MAVEN_JDK8' }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/raviteja811811/game-of-lifer.git',
                branch: 'try'
            }
        }
        stage ('build') {
            steps {
                sh 'mvn package'
            }
        }
        stage ('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                junit testResults:'**/surefire-reports/TEST-*.xml'
            }
        }
    }
}