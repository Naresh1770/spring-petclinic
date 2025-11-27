pipeline{
    agent { label 'node_1'}
          environmet{
               DOCKER_USER = credentials('dockerhub-cred')   
               }
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
          stage('Push to Dockerhub'){
                steps{
                   sh '''echo "$DOCKER_USER_PSW" | docker login -u "$DOCKER_USER_USR" --password-stdin
                    docker tag springpet-clinic:v1 $DOCKER_USER_USR/petclinic:v1
                    docker push $DOCKER_USER_USR/petclinic:v1 '''

                }
             }
        }
     }
