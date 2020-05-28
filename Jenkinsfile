pipeline {
   agent any
   tools{
       maven 'mvn'
       jdk 'jdk'
   }
   stages{
       stage("sync"){
           steps{
                git ('https://github.com/kudipudijahnavi/game-of-life')
           }
       }
       stage('build'){
           steps{
               sh "mvn clean package"
           }
       }
       stage('test'){
           steps{
                junit '**/target/surefire-reports/TEST-*.xml'
           }
       }
       stage('archive'){
           steps{
               archiveArtifacts 'gameoflife-core/target/*.jar'
           }
       }
   }
}
