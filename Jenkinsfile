pipeline {
    agent {label 'GOL'}
    stages {
        stage('SCM') {
            steps {
                git url: 'https://github.com/dileep208/dileepgameoflife.git'
            }
        }
        stage('build && SonarQube analysis') {
            steps {
                withSonarQubeEnv('SonarQube-sample-1') {
                    // Optionally use a Maven environment you've configured already
                    withMaven(maven:'Maven 3.6.0') {
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
        stage("Quality Gate") {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    // Parameter indicates whether to set pipeline to UNSTABLE if Quality Gate fails
                    // true = set pipeline to UNSTABLE, false = don't
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}