pipeline {
agent any
  stages {




        stage("Install Python Virtual Enviroment") {
            sh 'virtualenv --no-site-packages .'
        }


    stage ("Install Application Dependencies") {
        sh '''
            source bin/activate
            pip install -r requirements.txt
            deactivate
           '''
    }


    stage('test') {
      steps {
      sh '''
          source bin/activate
          sh 'python test.py'
          deactivate
         '''
      }
      post {
        always {
          junit 'test-reports/*.xml'
        }
      }
    }
  }
}
