pipeline {
    agent { label "slave1" }

    stages {
        stage('stage1_clone') {
            steps {
                echo 'clone my project'
                git 'https://github.com/shruthidevi/Helloworld-latest.git'
            }
        }
        stage('stage2_build') {
            steps {
                echo 'build my project'
                sh 'yum install maven -y'
                sh 'mvn -Dmaven.test.failure.ignore=true install'
            }
        }
        stage('stage3_deploy') {
            steps {
                echo 'deploy my project'
                deploy adapters: [tomcat8(credentialsId: 'tomcat_admin', path: '', url: 'http://54.243.17.254:8080/')], contextPath: null, war: '**/*.war'
            }
        }
        stage('stage4_test') {
            steps {
                echo 'test my project'
            }
        }
     }
}
