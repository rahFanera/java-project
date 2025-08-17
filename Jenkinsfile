pipeline {
    agent any
    stages {
        stage {
            steps {
                withSonarQubeEnv('sonar') {
                    sh "mvn -B sonar:sonar"
                }
            }
        }
    }
}