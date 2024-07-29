pipeline {
  agent {
    node {
      label 'agent01'
    }

  }
  stages {
    stage('stage1') {
      steps {
        sh '''echo "my first pipeline stage" 
echo " my DB username is $DB_username"'''
      }
    }

    stage('stage2') {
      steps {
        echo 'Pipeline is completed'
      }
    }

  }
  environment {
    DB_username = 'dbadmin'
  }
}