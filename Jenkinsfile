 pipeline {
 agent any
 stages {
 stage('Build') { 
steps {
 bat 'mvn clean package -DskipTests' 
}
 }
 stage('K8s') {
 steps {
 bat 'kubectl set image deployments/hello-node teedy2024-manual-grgv7=yang2003/teedy2024_manual'
 }
 }
 }
 }
