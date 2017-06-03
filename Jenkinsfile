node('unix') {
  properties([[$class: 'BuildDiscarderProperty', strategy: [$class: 'LogRotator', artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '10']]]);

  stage('Checkout') {
    checkout scm
  }

  def gitHome = pwd()

  stage('Generate') {
    sh "docker run --name hexo -d \
          -v /var/lib/jenkins/.ssh:/root/.ssh \
          -v /var/lib/jenkins/workspace/Docker_develop-G3XKBOIJ5T4KGI4WTC637QUICPXGXR5TKU76SITYPACLM7LRKP7Q/source:/Hexo/source \
          -v /var/lib/jenkins/workspace/Docker_develop-G3XKBOIJ5T4KGI4WTC637QUICPXGXR5TKU76SITYPACLM7LRKP7Q/themes:/Hexo/themes \
          -v /var/lib/jenkins/workspace/Docker_develop-G3XKBOIJ5T4KGI4WTC637QUICPXGXR5TKU76SITYPACLM7LRKP7Q/_config.yml:/Hexo/_config.yml \
          mikimoto/hexo  Mikimoto mikimoto.c@gmail.com"
  }
}