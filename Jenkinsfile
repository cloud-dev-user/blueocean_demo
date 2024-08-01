pipeline {
  agent {
    node {
      label 'agent01'
    }

  }
  stages {
    stage(" running stage1 and stage2 in parallel") {
    parallel {
      stage('stage1') {
      steps {
        sh '''echo "my first pipeline stage" 
echo " my DB username is $DB_username & my tagname is $tag_name"'''
      }
    }
    stage('stage2') {
      steps {
        echo 'This is parallel stage running along with stage1'
      }
    }
    }
    }
    
    stage('stage3') {
      steps {
        echo 'Pipeline is completed'
      }
    }

  }
  environment {
    DB_username = 'dbadmin'
  }
  parameters {
    string(name: 'tag_name', defaultValue: '', description: ' this is tag given to docker image')
  }
}
