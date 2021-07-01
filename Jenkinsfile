pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                sh 'mvn -f java-tomcat-sample-docker/pom.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
     Stage('Create docker tomcat Image'){
       steps{
           sh 'docker build . -t tomcatsamplewebapp:${env.BUILD_ID}'
           }
         }
}