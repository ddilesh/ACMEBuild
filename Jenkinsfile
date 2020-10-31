pipeline{
    agent any
    stages{
        stage('Checkout'){
            steps{
              git 'https://github.com/GopinathJayakumar/ACMEBuild'  
            }
        }
        stage('Maven Build'){
            steps{
                bat label: '', script: 'mvn clean install'
            }
        }
    }
    post{
        always{
            emailext body: 'Test Email',
            subject: 'Test',
            to: 'gopithri@gmail.com'
        }
    }
}
