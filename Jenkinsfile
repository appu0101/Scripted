node('built-in') 
{
   stage('ContinuousDownload')
   {
      git 'https://github.com/appu0101/Scripted.git'
   }
   stage('ContinuousBuild')
   {
     sh 'mvn package'
   }
   stage('ContinuousDeployment')
   {
     deploy adapters: [tomcat9(credentialsId: 'f8bdd284-8d4a-460b-bc2b-9544f29f0207', path: '', url: 'http://172.31.88.115:8080')], contextPath: 'testapp', war: '**/*.war'
   }
  stage('ContinuousTesting')
   {
     git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
     sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
   } 
   stage('Continuousdelivery')
   {
    input message: 'Need approval from DM', submitter: 'Ravi'
    deploy adapters: [tomcat9(credentialsId: 'f8bdd284-8d4a-460b-bc2b-9544f29f0207', path: '', url: 'http://172.31.87.155:8080')], contextPath: 'prodapp', war: '**/*.war'
   }
   
}
