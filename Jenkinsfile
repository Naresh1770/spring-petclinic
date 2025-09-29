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
                mail subject : 'your build was success',
                     body : 'your build was effective',
                     to : 'd.nareshyadav.1@gmail.com'
            }
            failure{
                mail subject : 'your build was failure',
                     body : 'your build was deffective',
                     to : 'd.nareshyadav.1@gmail.com'
            }
            aborted{
                mail subject : 'your build was stoped',
                     body : 'your build was aborted',
                     to : 'd.nareshyadav.1@gmail.com'
            }
        }
}