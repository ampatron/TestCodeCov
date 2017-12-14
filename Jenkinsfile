#!groovy
pipeline {
  agent any
  properties properties: [pipelineTriggers([]), [$class: 'GithubProjectProperty', displayName: 'Jenkins']]
  stages {
    stage('Test') {
      steps {
        step([$class: 'GitHubCommitStatusSetter', statusResultSource: [$class: 'ConditionalStatusResultSource', results: [[$class: 'BetterThanOrEqualBuildResult', message: 'Build success', result: 'PENDING', state: 'PENDING']]]])
        echo "hi"
      }
    }
  }
  post {
    success {
      step([$class: 'GitHubCommitStatusSetter', statusResultSource: [$class: 'ConditionalStatusResultSource', results: [[$class: 'BetterThanOrEqualBuildResult', message: 'Build success', result: 'SUCCESS', state: 'SUCCESS']]]])
    }
    failure {
      step([$class: 'GitHubCommitStatusSetter', statusResultSource: [$class: 'ConditionalStatusResultSource', results: [[$class: 'BetterThanOrEqualBuildResult', message: 'Build success', result: 'FAILURE', state: 'FAILURE']]]])
    }
  }
}
