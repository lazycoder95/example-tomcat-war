node('master')
{
  stage('SCM Checkout'){
    git 'https://github.com/lazycoder95/example-tomcat-war'
}
  stage('compile'){
    sh "mvn package"
  }  
  stage('Slack Notification'){
    slackSend baseUrl: 'https://hooks.slack.com/services/', botUser: true, channel: 'jenkins', color: 'good', message: 'hi', teamDomain: 'teamdemo-talk', tokenCredentialId: 'slackhookjen'
  }
}
