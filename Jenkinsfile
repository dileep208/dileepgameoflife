pipeline {
    agent {label 'GOL'}
    triggers {
        cron('H * * * *')
        pollscm('* * * * *')
    }
        stages {
            stage('scm') {
                steps {

                    git branch: 'master', url: 'https://github.com/dileep208/dileepgameoflife.git'
                }
            }
            stage('build') {
                steps {

                    sh 'mvn package'
                }
            }
        }
        post {
            success {

                archive '**/gameoflife.war'
                junit '**/TEST-*.xml'
            }
        }
}