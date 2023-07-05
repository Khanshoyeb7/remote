def remote = [:]
    remote.name = 'server'
    remote.host = '15.206.88.96'
    remote.allowAnyHosts = true

pipeline {
    agent any

    stages {
        stage('Remote SSH') {
            steps{
                script {
                    withCredentials([usernamePassword(credentialsId: 'ubuntucred', passwordVariable: 'pass', usernameVariable: 'user')]) {
                    remote.user = 'user'
                    remote.password = 'pass'
                    sshPut remote: remote, from: "index.html", into: "~"
                    sshCommand remote: remote, command: "ls -l"
                    }
                }
                }
            }
        }
}
