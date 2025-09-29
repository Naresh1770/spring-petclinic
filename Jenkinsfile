pipeline{
    agent any{
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
                    archiveArtifacts: '**/target/spring-petclinic-**-jar'    
                }
             }
        }
        post{
            success{
                echo 'your build was success'
            }
            failure{
                echo 'your build was unsuccess'
            }
            aborted{
                echo 'your build was stopped'
            }
        }
    }
}