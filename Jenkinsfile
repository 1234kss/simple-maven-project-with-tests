node('master'){  
   checkout scm
   stage('Build') { 
       //
       withMaven(maven: 'M3'){
       if(isUnix()){
           sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ifnore clean package"
        }else{
           bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ifnore clean package/)
          }
        }
      }
      stage('Results') { 
          // 
          junit '**/target/surefire-reports/TEST-*.xml' 
          archive 'target/*.jar'
      }
}
