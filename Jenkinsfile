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
        withSonarQubeEnv('sonar-quve-1') {
          sh "${scannerHome}/bin/sonar-scanner"
        }
      }
    
    }

  }
}

}  
