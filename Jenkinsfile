node('master') 
{
    stage ('contdownload')
    {
        git 'https://github.com/maheshallipuram/scripted-pipeline.git'
    }
    
    stage ('contbuild')
    {
        sh label: '', script: 'mvn  package'
    }
    
    stage ('contideploy')
    {
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/multibranch_master/webapp/target/webapp.war ubuntu@172.31.39.5:/var/lib/tomcat8/webapps/testapp.war'
    } 
    stage ('conttesting')
    {
        git 'https://github.com/maheshallipuram/selenium-in-CI-CD.git'
        sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/multibranch_master/testing.jar'
    }
    
    stage ('contdelivery')
    {
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/masterbranch_master/webapp/target/webapp.war ubuntu@172.31.82.59:/var/lib/tomcat8/webapps/prodapp.war'
    }
}
