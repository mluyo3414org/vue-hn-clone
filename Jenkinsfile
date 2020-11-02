pipeline {
  agent none
  options { 
    buildDiscarder(logRotator(numToKeepStr: '10'))
    skipDefaultCheckout true
  }
  stages('Node Test and Build')
  {
    stage('Node Tests') {
      agent {
        kubernetes {
          label 'nodejs'
       }
      }
      steps {
            checkout scm           
            container('nodejs') {
              sh '''
                 yarn install
                 yarn test:unit
                 '''
            }
      } 
    }
  }
}
