pipeline {
    agent { label 'JDK_8' }
    triggers { pollSCM ('H/30 * * * *') }
    parameters {
        choice(name: 'MAVEN_GOAL', choices: ['package', 'install', 'clean'], description: 'mavengoal')
    }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/raviteja811811/game-of-lifer.git',
                    branch: 'try'
            }
        }
        stage('package') {
            tools{
                jdk 'jdk_17'
            }
            steps {
                sh "mvn ${params.MAVEN_GOAL}"
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