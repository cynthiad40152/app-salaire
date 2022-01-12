node {

        stage('ansible init') {
                 sh "yum install -y ansible "

}
        stage('Ansible') {
    ansiblePlaybook (
    colorized: true, 
    become: true, 
    playbook: 'main.yaml',
    inventory: 'inventaire',
    disableHostKeyChecking: true
    )
  }

 }

