pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {
                git([url:'https://github.com/cynthiad40152/app-salaire'])
            }
        }
        
        stage ('Report') {
            parallel {
                stage('junit'){
                steps {
                    sh "/opt/apache-maven-3.5.4/bin/mvn clean test"
                }
                post {
                    always {
                junit 'server/target/surefire-reports/*.xml'
                    }
                }
                }
            }
        }

        
        stage('build') {
            steps {
            sh "/opt/apache-maven-3.5.4/bin/mvn test"
            sh "/opt/apache-maven-3.5.4/bin/mvn package" 
            sh "/opt/apache-maven-3.5.4/bin/mvn checkstyle:checkstyle"
            sh "/opt/apache-maven-3.5.4/bin/mvn findbugs:findbugs"
            }
            post {
                always {
                    step([$class: 'hudson.plugins.checkstyle.CheckStylePublisher', checkstyle: 'gitlist-PHP/build/logs/phpcs.xml'])
                }
            }
        }
        
        stage('Deploy') {
            steps {
            sh "/opt/apache-maven-3.5.4/bin/mvn deploy"
            }
        }
}
}
