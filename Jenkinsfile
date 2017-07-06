pipeline {
   agent any  
   def mvnHome = tool 'M3'
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
         sh "pwd"
         sh "ls"
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
}
