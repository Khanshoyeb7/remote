def remote = [:]
remote.name = 'test'
remote.host = '15.206.88.96'
remote.port = 22
remote.allowAnyHosts = true
pipeline {
    agent any
        stages {
            stage ('Remote Access') {
                steps {
                    script {
                        sh 'touch index.html'
                        sh 'ls'
                        withCredentials([usernamePassword(credentialsId: 'ubuntucred', passwordVariable: 'pass', usernameVariable: 'user')]) {
                            remote.user = user
                            remote.password = pass
                            sshCommand remote: remote, command: "mkdir ~/jenkins"
                            sshCommand remote: remote, command: "touch jenkins/file2"
                            sshCommand remote: remote, command: "ls ~/jenkins"
                        }
                    }
                }
            }
        }
}
