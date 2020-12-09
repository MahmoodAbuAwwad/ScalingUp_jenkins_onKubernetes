pipeline {
  agent {
    kubernetes {
      yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    some-label: jenkins
  name: jenkins
spec:
  containers:
  - name: jnlp
    image: jenkins/jnlp-slave
    tty: true
    workingDir: /home/jenkins/agent/

"""
    }
  }
  stages {
    stage('stage1') {
      steps {
        container('jnlp') {
            sleep(30)
            sh('pwd')
        }
      }
    }
  }
}

