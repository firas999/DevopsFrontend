pipeline{
    agent any
    
    stages{
       stage('GetCode'){
            steps{
                script{
                    checkout   ([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/firas999/AngulaProject.git']]])
	sh "whoami"               
 }
               
            }
         }      
 stage('build'){
steps{
script{
  sh "npm install"

sh "ansible-playbook ansible/build.yml  -i ansible/inventory/host.yml -e 'ansible_become_password=ansible' -vvv   " 

}
}
}      
       
stage ('docker'){
steps{
script{
sh "ansible-playbook ansible/docker.yml  -i ansible/inventory/host.yml -e 'ansible_become_password=ansible'     "
}
}
}
}
}
