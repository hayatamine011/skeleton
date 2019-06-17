pipeline {
    agent { label 'ansible' }
    tools {
        maven 'Maven 3.3.9'
        jdk 'jdk1.8.0'
    }
    stages {
        stage('Build') {
          //  parallel {
              //  stage('Build Backend'){
                    steps {
                        dir('backend'){
                            sh 'mvn --settings settings.xml clean install spotbugs:spotbugs checkstyle:checkstyle deploy'
                        }
                    }

              //  }
              //  stage('Build Frontend'){
                    steps {
                        dir('frontend'){
                            sh 'npm install --save'
                            sh 'npm install jest-cli --save'
                            sh 'mvn --settings settings.xml clean install'
                        }
                    }
                }
          //  }
       // }
        stage('Deploy to test'){
            steps {
                dir('deployment'){
                    echo 'Deploying to test'
                    sh 'ansible-playbook -i dev-servers site.yml'
                }
            }
        }
        stage('API tests'){
            steps {
                echo 'Executing API tests'
            }
        }
        stage('Performance tests'){
            steps {
                echo 'Executing Performance tests'
            }
        }
    }
}
