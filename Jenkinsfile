node('unix') {
  properties([[$class: 'BuildDiscarderProperty', strategy: [$class: 'LogRotator', artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '10']]]);

  stage('Checkout') {
    checkout scm
  }

  def gitHome = pwd()

  stage('Generate') {
    try {
      sh "docker rm hexo"
    } catch(e) {

    }
    
    sh "docker run --name hexo -d \
          -v /var/lib/jenkins/.ssh:/root/.ssh \
          -v ${gitHome}/source:/Hexo/source \
          -v ${gitHome}/themes:/Hexo/themes \
          -v ${gitHome}:/root/hexo \
          mikimoto/hexo  Mikimoto mikimoto.c@gmail.com"
  }
}