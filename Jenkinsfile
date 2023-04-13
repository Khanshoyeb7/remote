def remote = [:]
    remote.name = 'server'
    remote.host = '3.110.175.3'
    remote.allowAnyHosts = true

pipeline {
    agent any

    stages {
        stage('Remote SSH') {
            steps{
                    remote.user = 'shoyeb'
                    remote.password = 'pass'
                    sshPut remote: remote, from: "index.html", into: "~"
                    sshCommand remote: remote, command: "ls -l"
                }
            }
        }
}
