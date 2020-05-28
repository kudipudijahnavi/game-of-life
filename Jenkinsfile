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
              when {
		 beforeInput true
                 branch 'dev/januPL'
		}
		input {
		    message " this will happen only when branch is dev/januPL"
                    id "user-input"
		}
               archiveArtifacts 'gameoflife-core/target/*.jar'
           }
       }
   }
}
