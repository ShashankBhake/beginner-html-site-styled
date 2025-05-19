pipeline {
  agent any
  stages {
    stage("Build") {
      steps {
        sh "docker build -t html-site ."
      }
    }
    stage("Run") {
      steps {
        sh "docker stop html-site || true"
        sh "docker rm html-site || true"
        sh "docker run -d --name html-site -p 99:80 html-site"
      }
    }
  }
  triggers {
    pollSCM("* * * * *")  # Check for GitHub changes every minute
  }
}
