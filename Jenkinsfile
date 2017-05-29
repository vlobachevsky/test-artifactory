#!/usr/bin/env groovy

node {

  stage('Build') {
    gitCheckout()
    gradlew('build')
  }
}

def gitCheckout() {
  checkout([$class: 'GitSCM',
      branches: [[name: '*/master']],
      doGenerateSubmoduleConfigurations: false,
      extensions: [],
      submoduleCfg: [],
      userRemoteConfigs: [[url: 'https://github.com/vlobachevsky/test-artifactory.git']]]
  )
}

def gradlew(String... args) {
    sh 'chmod a+x ./gradlew'
    withEnv(["GRADLE_USER_HOME=${pwd()}/.gradlehome", 'TZ="America/New_York"']) {
        sh "./gradlew ${args.join(' ')} --no-daemon --parallel --stacktrace"
    }
}
