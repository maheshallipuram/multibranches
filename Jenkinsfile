node('master') 
{
    stage('ContDownload') 
    {
       git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('ContBuild')
    {
        sh label: '', script: 'mvn package'
    }
    stage('ContDeployment')
    {
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.92.242:/var/lib/tomcat8/webapps/testapp.war'
    }
    stage('ContTesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
    }
    stage('ContDelivery')
    {
       sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.88.41:/var/lib/tomcat8/webapps/prodapp.war' 
    }
    
}
