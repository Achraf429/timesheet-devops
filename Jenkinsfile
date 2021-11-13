pipeline{

   agent{label 'windows' }

   options{
    buildDiscarder{ logRotator(numTokeepStr: '5')}

}
  environment {
DOCKERHUB_CREDENTIALS = credentials('darinpope-dockerhub')

}
stages {

 stage('build'){
steps{
 sh 'docker build -f Dockerfile -t docker-spring-boot.jar .'
}
}
 stage('Login'){
steps{
sh 'echo $DOCKERHUB_CREDENTIALS_PW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-root'
}
}
stage('Push'){
  steps{
sh 'docker push 193jmt2074/docker-spring-boot.jar'
}
}
}
post {
always{
sh 'docker logout'
}
}
}
