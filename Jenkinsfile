node {
  def app

  stage('Clone repository') {
    /* Let's make sure we have the repository cloned to our workspace */

    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
      doGenerateSubmoduleConfigurations: false,
      extensions: [], submoduleCfg: [],
      userRemoteConfigs: [[url: 'https://github.com/devopsgod/4']]])
  }

  stage('Build image') {
    /* This agent directive tells Jenkins to allocate an executor and workspace for the pipeline on any available agent */

    app = docker.build("eureka")
  }

  stage('Deploy image') {
    bat(script: 'C:\\Windows\\System32\\cmd.exe /c docker rm -f eureka')
    bat(script: 'C:\\Windows\\System32\\cmd.exe /c docker run -d -p 8761:8761 --name eureka eureka')
  }
}
