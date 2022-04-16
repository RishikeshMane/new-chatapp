pipeline {
agent any
 stages {
  stage('Build') {
   steps {
    sh 'rsync -av -e "ssh -o StrictHostKeyChecking=no -i /var/lib/jenkins/new-backend1.pem" /var/lib/jenkins/workspace/New_pipeline/  ubuntu@10.0.3.179:/home/ubuntu/new_chatapp'
   }
 }
stage ("SonarQube Analysis") {
            steps {
                script {
                    def scannerHome = tool 'sonar-scanner';
                    withSonarQubeEnv('sonarqube') { 
                         sh "${tool("sonar-scanner")}/bin/sonar-scanner -Dsonar.projectKey=chatapp -Dsonar.projectName=chatapp"  
                    }
                }
            }
        } 
 stage('Deploy') {
  steps {
   sh 'ssh -i /var/lib/jenkins/new-backend1.pem ubuntu@10.0.3.179 sudo systemctl restart gunicorn'
  }
 }
}
}
