pipeline {
environment {
registry = "ahmedmongey/myrepo"
registryCredential = 'DockerHub'
dockerImage = ''
}
agent any
stages {
stage('Cloning our Git') {
steps {
git 'https://github.com/ahmedmongey/nodeapp.git'
}
}
stage('Building our image') {
steps{
script {
dockerImage = docker.build registry + ":$BUILD_NUMBER"
}
}
}
stage('Deploy our image') {
steps{
script {
docker.withRegistry( '', registryCredential ) {
dockerImage.push()
stage('Deploy to K8s')
  {
   steps{
    sshagent(['k8s-jenkins'])
    {
     sh 'scp -r -o StrictHostKeyChecking=no deployment.yaml ec2-user@54.165.89.154:/path'
      script{
      try{
       sh 'ssh ec2-user@54.165.89.154 kubectl apply -f /path/node-deployment.yaml --kubeconfig=/path/kube.yaml'}catch(error)
       {}
     }
    }
   }
  }
