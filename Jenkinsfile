node
{
def mavenHome = tool name: "Maven3.6.3"
stage ('codecheckout')
{
 git 'https://github.com/ramdasnaikdevops2/maven-web-application.git'
}
stage ('Bulding')
{
 sh "${mavenHome}/bin/mvn clean package"
}

stage ('deployment')
{
sshagent(['5dd2bac9-1d1c-4b11-b133-e776cbaf113e']) 
{
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.233.89.167:/opt/tomcat9/webapps/"      
}
}
stage ('sending email notification')

{
emailext body: '''Regards

Ramadas Naik
DevOps ENG''', subject: 'Build over ', to: 'ramdasnaik1122@gmail.com'
}
}
