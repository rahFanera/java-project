pipeline {
    agent any
    stages {
        stage('Quality Analysis') {
            steps {
                withSonarQubeEnv('sonar') {
                    sh "mvn -B sonar:sonar"
                }
            }
        }
        stage('Artifact') {
            steps {
                sh "mvn package"
            }
        }
        stage('Artifact Upload'){
            steps{
                nexusArtifactUploader artifacts: [[artifactId: 'javaproject', classifier: '', file: 'javaproject.jar', type: '.jar']], credentialsId: 'nexus', groupId: 'org.example', nexusUrl: 'localhost:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'https://github.com/rahFanera/java-project', version: '4.0.0'
            }
        }
    }
}
