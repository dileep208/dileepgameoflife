pipeline {
    agent {label 'GOL'}
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
            sucess {
                
                archive '**/*.war'
                junit '**/TEST-*.xml'
            }
        }
}