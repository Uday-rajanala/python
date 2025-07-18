pipeline{
  agent any
  environments{
    IMAGE=uday
    VERSION=${build_number}
  }
  stages{
    stage('clone_repo'){
      steps{
        sh 'echo "clone the repository "'
      }
  }
    stage('build image'){
      steps{
        sh'docker build -t $IMAGE : $VERSION .'
    }
  stage('build_container'){
    steps(
      sh'docker run --name container1 -dp  5000:5000 $IMAGE :$VERSION '
    )
  }
}
