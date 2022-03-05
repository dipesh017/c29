pipeline {
  agent any
  stages {
    stage('Git Pull') {
      steps {
        echo 'Git Pull Doing'
        sleep 2
      }
    }

    stage('UnitTesting Linux') {
      parallel {
        stage('UnitTesting Linux') {
          steps {
            echo 'doing unit testing linux'
          }
        }

        stage('Unit Testing Windows') {
          steps {
            echo 'Unit Testing Windows'
            sh 'echo "Unit Testing Windows"'
          }
        }

      }
    }

    stage('Dokcer Build') {
      steps {
        sh 'docker build .'
      }
    }

    stage('Docker push') {
      steps {
        sh 'docker push '
      }
    }

  }
  environment {
    ECR_CLUSTER_NAME = 'upgrad'
    ECS_SERVICE_NAME = 'vote'
  }
}