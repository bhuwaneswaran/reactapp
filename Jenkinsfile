node {
  try {
    stage('Checkout') {
      checkout scm
    }
    stage('Environment') {
      sh 'git --version'
      echo "Branch: ${env.BRANCH_NAME}"
      sh 'docker -v'
      sh 'printenv'
    }
   
    stage('Deploy'){
     
        sh 'docker build -t reactapp --no-cache .'
        sh 'docker tag reactapp localhost:5000/reactapp'
        sh 'docker push localhost:5000/reactapp'
        sh 'docker rmi -f reactapp localhost:5000/reactapp'
      
    }
  }
  catch (err) {
    throw err
  }
}
