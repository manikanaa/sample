pipeline {
    agent any

    tools {
        maven 'M2_HOME'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
         stage('Archiveartifact') {
             steps {
               // archiveArtifacts artifacts: 'target/*.war', onlyIfSuccessful: true
                  archiveArtifacts artifacts: 'target/*.war'
             }
         }
                 stage ('Copy .war file to tomcat') {
             steps {
                 echo ''
                 // bat '''copy target\\*.war C:\\apache-tomcat-8.5.42-windows-x64\\apache-tomcat-8.5.42\\webapps\\'''
                 //sh 'ssh ec2-user@ && sudo -i && helm upgrade first ./firstrepo && kubectl get all -o wide'
                  // sshCommand command: "ls -lrt"
                 sh '''
                       cd /etc/ansible
                       ansible-playbook deploy.yml
                    '''
             }
         }
        stage ('Restarting application') {
             steps {
                 echo ''
                 // bat '''copy target\\*.war C:\\apache-tomcat-8.5.42-windows-x64\\apache-tomcat-8.5.42\\webapps\\'''
                 //sh 'ssh ec2-user@ && sudo -i && helm upgrade first ./firstrepo && kubectl get all -o wide'
                  // sshCommand command: "ls -lrt"
                 sh '''
                       cd /etc/ansible
                       ansible-playbook deploy1.yml
                    '''
             }
         }
    }
}
