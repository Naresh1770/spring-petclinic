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
                    Mail(
                        subject : "APPLICATION SUCCESS",
                        body :"Your application is running Success",
                        to :"d.nareshyadav.1@gmail.com"
                    )
                }
                failure{
                    Mail(
                        subject : "APPLICATION FAILE",
                        body :"Your application was Failed",
                        to :"d.nareshyadav.1@gmail.com"
                    )
                }
                aborted{
                  Mail(
                        subject : "APPLICATION ABORTED",
                        body :"Your application was Stopped",
                        to :"d.nareshyadav.1@gmail.com"
                    )  
                }

                
             }
        
}