 pipeline {
 agent any
 stages {
 stage('Build') { 
steps {
 sh 'mvn -B -DskipTests clean package' 
}
 }
 stage('K8s') {
 steps {
 sh 'kubectl set image deployments/hello-node teedy2024-manual-grgv7=yang2003/teedy2024_manual'
 }
 }
 }
 }
