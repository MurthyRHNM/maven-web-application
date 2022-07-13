node{
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

def mavenHome= tool name: "maven3.8.6"

stage('CheckoutCode'){
git branch: 'development', credentialsId: 'c8681f19-2107-43c7-8bca-845e4df2137d', url: 'https://github.com/MurthyRHNM/maven-web-application.git'
}

stage('Build'){
sh"${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubeReport'){
sh"${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('UploadAtrifactIntoNexusRepo'){
sh"${mavenHome}/bin/mvn clean deploy"
}
stage('DeployApplicationIntoTomcatServer'){
 sshagent(['5dbc9ec0-07ed-4904-a213-2bda5229bb29']){
 sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.110.194.50:/opt/apache-tomcat-9.0.64/webapps/"
}
}
*/
}
