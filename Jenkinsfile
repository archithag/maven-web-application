node {
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
    def meavenhome = tool name: "maven3.9.4"
    stage('Checkoutcode'){
        git branch: 'development', credentialsId: '3204d058-9ed5-4ca4-a2e7-7215ecd36cdb', url: 'https://github.com/archithag/maven-web-application.git'
    }
    stage('Build'){
        sh "${meavenhome}/bin/mvn clean package"
    }
    /*
    stage('Sonar'){
        sh "${meavenhome}/bin/mvn clean sonar:sonar"
    }
    stage('Nexus'){
        sh "${meavenhome}/bin/mvn clean deploy"
    }
    stage('Tomcat'){
    sshagent(['96a4ef4b-b6d6-4c53-b9bd-01ada43d9255']) {
        sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.89.176:/opt/apache-tomcat-9.0.80/webapps"
    }
    }
    */
}
