pipeline{
    agent any
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
        post{
            success{
                mail( 
                    subject : 'Build success',
                     body : 'your build was effective',
                     to : 'd.nareshyadav.1@gmail.com'
                     )
            }
            failure{
                mail (
                     subject : 'Build failure',
                     body : 'please check jenkins logs',
                     to : 'd.nareshyadav.1@gmail.com'
                )
            }
            aborted{
                mail ( 
                    subject : 'Build aborted',
                     body : 'your build was stopped',
                     to : 'd.nareshyadav.1@gmail.com'
                )
            }
        }
}