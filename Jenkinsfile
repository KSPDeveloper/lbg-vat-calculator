pipeline {
  agent any

  stages {
    stage('Checkout')
    {
      steps {
        git branch: 'main', url: 'https://github.com/KSPDeveloper/lbg-vat-calculator.git'
      }
    }
    stage('SonarQube Analsis')
    {
      environment {
       scannerHome = tool 'sonarqube'   
      }
      steps {
        withSonarQubeEnv('sonar-qube-kyle') {
          sh "${scannerHome}/bin/sonar-scanner"
        }
      }
    
    }

  }
}

}  
