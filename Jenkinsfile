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

        stage('Build') {
            steps{
                sh "mvn compile"
            }
        }

        stage('Artifact') {
            steps {
                sh "mvn clean package"
                sh "echo '--- Vérification du contenu du dossier target/ ---'"
                sh "ls -lh target/"
            }
        }

        stage('Artifact Upload') {
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'java-project', classifier: '', file: '/java-project/target/javaproject-1.0-SNAPSHOT.jar', type: '.jar']], credentialsId: 'nexus', groupId: 'org.example', nexusUrl: 'localhost:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'https://github.com/rahFanera/java-project', version: '4.0.0'
            }
        }
    }
}
