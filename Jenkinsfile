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
}