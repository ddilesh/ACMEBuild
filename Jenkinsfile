pipeline {
  agent any
  stages {
    stage('Checkout from Git') {
      steps {
        echo 'Checkout from Git'
        git(url: 'https://github.com/ddilesh/ACMEBuild', branch: 'master')
      }
    }

    stage('Run Smoke Test') {
      steps {
        echo 'Smoke Test Run Started'
        git(url: 'https://github.com/ddilesh/EyeAutomation', branch: 'master', poll: true)
        bat 'mvn test -DEnvironment=QA'
      }
    }

    stage('UI Test') {
      parallel {
        stage('UI Test') {
          steps {
            echo 'UI Test Success'
          }
        }

        stage('API Test') {
          steps {
            echo 'API Test Success'
          }
        }

        stage('Performance Test') {
          steps {
            echo 'Performnce Test Success'
          }
        }

      }
    }

    stage('Deploy to QA') {
      steps {
        echo 'QA Certified Success'
      }
    }

    stage('Manual Certify') {
      when {
        branch 'master'
      }
      steps {
        input(message: 'Manual Certification', ok: 'Yes')
      }
    }

  }
  post {
    always {
      emailext(body: 'Test Email', subject: 'Test', to: 'ddilesh@gmail.com')
    }

  }
}