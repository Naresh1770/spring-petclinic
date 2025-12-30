pipeline{
    agent any
    options{
      timeout{time: 1, unit: 'HOURS'}
    }
    stages{
      stage(git){
         steps{
            git url: 'github.com/Naresh1770/spring-petclinic.git'
                branch: 'main'
         }
      }
      stage(MVN){
         steps{
            sh 'mvn package'
         }
      }
      stage(downloading){
         steps{
          archiveArtifacts artifacts: '**/target/spring-petclinic-*.jar'
         }
      }
    }
     post { 
        success { 
            mail(
                subject: 'build success'
                body: 'Your build was success'
                to: 'nareshyadav1770@gmail.com'
             )
        }
        failure { 
            mail(
                subject: 'build fail'
                body: 'Your build was fail'
                to: 'nareshyadav1770@gmail.com'
             )
        }
    }
}