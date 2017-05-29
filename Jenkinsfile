#!/usr/bin/env groovy

node {

  stage('Build') {
    gradlew('build') 
  }
}

def gradlew(String... args) {
    sh 'chmod a+x ./gradlew'
    withEnv(["GRADLE_USER_HOME=${pwd()}/.gradlehome", 'TZ="America/New_York"']) {
        sh "./gradlew ${args.join(' ')} --no-daemon --parallel --stacktrace"
    }
}
