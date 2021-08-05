pipeline {
    agent {label 'GOL'}
    triggers {
        cron('H * * * *')
        pollSCM('* * * * *')
    }
        stages {
            stage('scm') {
                steps {

                    git branch: 'master', url: 'https://github.com/dileep208/dileepgameoflife.git'
                    input 'Continue to the next stage? '
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