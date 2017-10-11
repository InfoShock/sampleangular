#!groovy

pipeline {

  agent any

  environment {
    git_commit_message = ''
    git_commit_diff = ''
    git_commit_author = ''
    git_commit_author_name = ''
    git_commit_author_email = ''
  }

  stages {

    // Build
    stage('Build') {
      steps {
        deleteDir()
        checkout scm
	sh "npm install"
	sh "ng build"
      }
    }

    // Static Code Analysis
    stage('Static Code Analysis') {
      steps {
        deleteDir()
        checkout scm
        sh "echo 'Run Static Code Analysis'"
      }
    }

    // Unit Tests
    stage('Unit Tests') {
      steps {
        deleteDir()
        checkout scm
        sh "echo 'Run Unit Tests'"
      }
    }

    // Acceptance Tests
    stage('Acceptance Tests') {
      steps {
        deleteDir()
        checkout scm
        sh "echo 'Run Acceptance Tests'"
      }
    }

  }
  post {
    success {
      mail to:"john.knight@infosys.com", subject:"SUCCESS: ${currentBuild.fullDisplayName}", body: "Yay, we passed."
    }
    failure {
      mail to:"john.knight@infosys.com", subject:"FAILURE: ${currentBuild.fullDisplayName}", body: "Boo, we failed."
    }
  }
}
