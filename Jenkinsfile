pipeline {
    agent any
    
    tools
    {
       maven "mvn"
    }
     
    stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/puneetbhatia77/CI-addressbook-deploy-usingAnsible.git'
             
          }
        }
         stage('Tools Init') {
            steps {
                script {
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
               def tfHome = tool name: 'Ansible'
                env.PATH = "${tfHome}:${env.PATH}"
                 sh 'ansible --version'
                    
            }
            }
        }
     
        
         stage('Execute Maven') {
           steps {
             
                sh 'mvn package'             
          }
        }
        
        
         
        
        
        
        stage('Ansible Deploy dev') {
             
            steps {
                 
             
               
               sh "ansible-playbook main.yml -i inventories/dev/hosts --user ubuntu --key-file ~/.ssh/id_rsa"

               
            
            }
        }
        
        
         stage('Ansible Deploy prod') {
             
             steps {
                 
             
               
               sh "ansible-playbook main.yml -i inventories/prod/hosts --user ubuntu --key-file ~/.ssh/id_rsa"

             
    }
   
}
        
        
        
    }
}
