#!/usr/bin/env groovy

node {

  stage('Build') {
    checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/vlobachevsky/test-artifactory.git']]])
    gradlew('build') 
  }
}

def gradlew(String... args) {
    sh 'chmod a+x ./gradlew'
    withEnv(["GRADLE_USER_HOME=${pwd()}/.gradlehome", 'TZ="America/New_York"']) {
        sh "./gradlew ${args.join(' ')} --no-daemon --parallel --stacktrace"
    }
}
