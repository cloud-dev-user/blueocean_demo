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
echo " my DB username is $DB_username & my tagname is $tag_name"'''
      }
    }

    stage('stage2') {
      when {
           branch 'master'
            }
      steps {
        echo 'Pipeline is completed'
      }
    }
    stage('stage3') {
      steps{
             withCredentials(bindings: [string(credentialsId: 'my-creds', variable: 'TOKEN')]) {
            sh "echo $TOKEN"
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
