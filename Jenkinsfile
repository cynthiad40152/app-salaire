node {

        stage('ansible init') {
                 sh "yum install -y ansible "

}
        stage('ansible') {
                 sh "ansible-playbook main.yml -i inventaire --user jenkins --key-file ~/.ssh/id_rsa "

}

 }

