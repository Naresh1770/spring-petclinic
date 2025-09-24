pipeline{
    agent any
    options{
        timeout(time: 10, unit: 'HOURS')
    }
    triggers{
        pollSCM('* * * * *')
    }
    tools{
        jdk 'JDK_8'
    }
    stages{
        stage ('git') {
            steps{
                git url: 'https://github.com/Naresh1770/spring-petclinic.git',
                branch: 'main'
            }
        }
        stage ('MVN') {
            steps{
                sh script: 'mvn package'
            }

        }
    }
}