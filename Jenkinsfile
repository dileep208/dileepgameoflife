node('GOL') {
    
    stage('scm') {
    git 'https://github.com/dileep208/dileepgameoflife.git'
    }
    stage('build') {
        sh 'mvn package'
    }
    stage('post build') {
        archive '**/*.war'
        junit '**/TEST-*.xml'

    }
}