pipeline{
    agent any
    tools {
        jdk 'JDK'
        maven 'Maven 1'
    }
    stages {
        stage ('PULL THE APPLICATION FROM GITHUB') {
            steps {
                git branch: 'vp-rem', url: 'https://github.com/zanmin2018/ci-project1.git'
            }
        }
        stage ('BUILD THE APPLICATION') {
            steps {
                sh 'mvn -s settings.xml install -DskipTests' 
            }
            post {
                success{
                    echo 'New achiving'
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage ('TEST') {
            steps {
                sh ' mvn test'
            }
            post{
                success {
                    slackSend channel: '#ci-project',
                    color:'good',
                    message: "TEST IS SUCCESS"
                }
                failure {
                    slackSend channel: '#ci-project',
                    color: 'danger',
                    message: "TEST IS FAILED"
                }
            }
        }
        stage ('UNIT TEST') {
            steps {
                sh 'mvn test'
            }
        }
        stage ('INTEGRATION TEST') {
            steps {
                sh 'mvn verify -DskipUnitTest'
            }
        }
    }
}
