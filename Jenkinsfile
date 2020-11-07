pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh '/usr/local/maven/bin/mvn -s /usr/local/maven/conf/settings.xml -gs /usr/local/maven/conf/settings.xml -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh '/usr/local/maven/bin/mvn -s /usr/local/maven/conf/settings.xml -gs /usr/local/maven/conf/settings.xml test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
