pipeline{
    agent { label 'node_1'}
        stages{
            stage('git'){
                steps{
                    git url: 'https://github.com/Naresh1770/spring-petclinic.git',
                     branch: 'main'
                }
            }
             stage('MVN'){
                steps{
                    sh script: 'mvn package'      
                }
             }
             stage('docker build'){
                steps{    
                   sh 'docker build -t springpet-clinic:v1 .'

                }
             }
        }
     }
