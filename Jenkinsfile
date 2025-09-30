pipeline{
    agent { label 'Node_14.0.0.7' }
        options{
             timeout(time: 10 , unit:'MINUTES')
        }
        triggers{
            pollSCM('* * * * *' )
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
             stage('downloading'){
                steps{    
                    archiveArtifacts artifacts: '**/target/spring-petclinic-*.jar'

                }
             }
        }
}