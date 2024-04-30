pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'mvn -B clean package'
            }
        }
        stage('Run Tests') {
            steps {
                bat 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/**/*.xml'
                    archiveArtifacts artifacts: 'target/surefire-reports/**/*.xml', fingerprint: true
                }
            }
        }
        stage('Static Analysis') {
            steps {
                bat 'mvn pmd:pmd'
            }
            post {
                always {
                    archiveArtifacts artifacts: 'target/site/**', fingerprint: true
                }
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
