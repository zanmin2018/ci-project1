pipeline{
    agent any
    tools {
        jdk 'jdk'
        maven 'Maven'
    }
    stages {
        stage ('PULL THE APPLICATION FROM GITHUB') {
            steps {
                git branch: 'vp-rem', url: 'https://github.com/zanmin2018/ci-project1.git'
            }
        }
        stage ('BUILD THE APPLICATION') {
            steps {
                sh 'mvn install -DskipTests' 
            }
        }
        stage ('TEST') {
            steps {
                sh ' mvn test'
            }
        }
        stage ('UNIT TEST') {
            steps {
                sh 'mvn test'
            }
        }
        stage ('INTEGRATION TEST') {
            steps {
                sh 'mvn -DskipUnitTest'
            }
        }
    }
}
