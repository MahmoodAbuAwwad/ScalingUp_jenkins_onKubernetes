@Library("k8sagent@v0.1.0")
pipeline {
  agent {
    kubernetes(k8sagent(name: 'kubernetes'))
  }
  stages {
    stage('demo') {
      steps {
        echo "this is a demo"
        script {
          container('pg') {
            sh 'su - postgres -c \'psql --version\''
          }
        }
      }
    }
  }
}
