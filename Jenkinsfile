node('master')
{
  stage('SCM Checkout'){
    git 'https://github.com/lazycoder95/example-tomcat-war'
}
  stage('compile'){
    def mvnhome = tool name: 'mvn3', type: 'maven'
    sh "${mvnhome}/bin/mvn package"
  }  
  stage('mail'){
    mail bcc: '', body: 'The job is currently processed.', cc: '', from: '', replyTo: '', subject: 'jenkins job status', to: 'devas.5991@gmail.com'
  }
  stage('copy to salve'){
    sshagent(['slavemachine']) {
    sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@3.237.188.247:/home/ubuntu/apache-tomcat-9.0.72/webapps/'
    }
  }
}

node('slave')
{
  stage('test'){
    sh 'pwd > new.txt'
  }
}
