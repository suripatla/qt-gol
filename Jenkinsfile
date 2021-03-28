pipeline {
    agent { label 'ltecomm'}
    stages {
        stage('scm') {
            steps {
                git branch: 'qa', url:'https://github.com/suripatla/qt-gol.git'        
            }
        }
        stage('build') {
            steps {
                sh script: 'mvn clean package'
            }
        }
        stage('post build') {
            steps {
                junit 'gameoflife-web/target/surefire-reports/*.xml'
                archiveArtifacts 'gameoflife-web/target/*.war'
            }
        }
    }
}