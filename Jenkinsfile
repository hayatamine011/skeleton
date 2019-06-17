pipeline {
    agent { label 'ansible' }
    tools {
        maven 'Maven 3.3.9'
        jdk 'jdk1.8.0'
    }
    stages {
        stage('Build') {
          //  parallel {
                stage('Build Backend'){
                    steps {
                        dir('backend'){
                            sh 'mvn --settings settings.xml clean install spotbugs:spotbugs checkstyle:checkstyle deploy'
                        }
                    }

                }
               
}
    }
