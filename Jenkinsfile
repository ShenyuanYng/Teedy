pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'mvn -B clean package'
            }
        }
     
      
        stage('Generate Javadoc') {
            steps {
                bat 'mvn javadoc:jar'
            }
            post {
                always {
                    archiveArtifacts artifacts: 'target/site/apidocs/**', fingerprint: true
                }
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: '**/target/**/*.jar', fingerprint: true
            archiveArtifacts artifacts: '**/target/**/*.war', fingerprint: true
        }
    }
}
