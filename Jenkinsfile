pipeline {
  agent any
  environment{
    DEPLOY_TO='Stage'
  }
  stages {
    stage('build') {
      steps{
       retry(5){
       timeout(time: 10, unit: 'SECONDS')
       echo "Build done"
       sleep 5
       }
      }
    }
    stage ('deploy to dev') {
      echo " deployed to dev"
    }
    stage ('deploy to test') {
      steps{
      when {
        equals expected:'Stage',actual: "${DEPLOY_TO}"
      }
       echo " deploying to test env"
      }
      
    }
    stage ('deploy to stage') {
      steps{
        when {
          BRANCH_NAME==~/(hotfix|stage)/
        }
        echo " deployed to stage"
      }
      
    }
  }
}
