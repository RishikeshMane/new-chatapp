pipeline {
agent any
 stages {
  stage('Build') {
   steps {
    sh 'rsync -av -e "ssh -o StrictHostKeyChecking=no -i /var/lib/jenkins/sanmay.pem" /var/lib/jenkins/workspace/mypipeline-chattapdb/         ubuntu@172.31.4.193:/home/ubuntu/new_chatapp'
   }
 }
 stage('Deploy') {
  steps {
   sh 'ssh -i /var/lib/jenkins/sanmay.pem ubuntu@172.31.4.193 sudo systemctl restart gunicorn'
  }
 }
}
}
