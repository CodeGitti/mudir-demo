pipeline{
  agent{
    node {label 'slave'}
  }
  stages{
    stage('clone repo'){
      steps{
          git 'https://github.com/CodeGitti/mudir-demo.git'
          sh 'pwd'
      }
    }
    stage('Build the project'){
      steps{
          sh 'mvn clean package'
          sh 'pwd'
      }
    }
   stage('Deploy the project'){
     steps{
       sh 'echo "Begin Deploy"'
       sh 'sudo cp /home/jenkins/jenkins_slave/workspace/mudir-pipeline/webapp/target/webapp.war /home/ubuntu/apache-tomcat-9.0.87/webapps'
        sh 'sudo /home/ubuntu/apache-tomcat-9.0.87/bin/shutdown.sh'
        sh 'sleep 6'
        sh 'sudo /home/ubuntu/apache-tomcat-9.0.87/bin/startup.sh'
        sh 'echo "Completed"'
     }
   }
 }
}
