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
stage('Deploy to kubernetes') {
steps {
script{
kubernetesDeploy(configs: "deployment.yml" , kubeconfigID: "kubernetes")
}
}
}
}
}
}
}
}
}
