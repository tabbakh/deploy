node {
    def host
    def credentialsId

    if ("${params.environment}" == "production") {
        host = 'prod'
        credentialsId = 'azure-credentials'
    } else {
        host = 'staging'
        credentialsId = 'azure-vm2'
    }

    stage('Deploiement Ansible') {
        ansiblePlaybook(
            playbook: 'playbooks/azure.yaml',
            inventory: 'inventories/azure.txt',
            credentialsId: credentialsId ,
            extras: '--extra-vars "short_commit_hash=' + "${params.tag}" +' host='+ host +'"'
        )
    }
}
