node {
        stage('checkout') {
            git 'https://github.com/cynthiad40152/app-salaire/*main'
        }

        
        stage('ansible') {
          ansiblePlaybook (
          colorized: true, 
          become: true, 
          playbook: 'main.yaml',
          inventory: 'inventaire'
 )
 }
        
}

