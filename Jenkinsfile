node
{

def mavenHome = tool name: "maven3.8.6" 
echo "jenkinsjobnameis: ${env.JOB_NAME}"
properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
stage('CheckoutCode'){
git branch: 'development', url: 'https://github.com/meghana4-g/maven-web-application.git'
}

stage('build'){
sh "${mavenHome}/bin/mvn clean package"
}
stage('executeSonar'){
sh "${mavenHome}/bin/mvn sonar:sonar"
}
stage ('deploynexus'){
sh "${mavenHome}/bin/mvn deploy"

}


}
