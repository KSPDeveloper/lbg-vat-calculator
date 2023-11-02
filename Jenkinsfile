pipeline {
  agent any
    tools { 
        maven "M3"
      }
  stages {
    stage('Checkout')
    {
      steps {
        git branch: 'main', url: 'https://github.com/KSPDeveloper/lbg-vat-calculator.git'
      }
    }
    stage('Install'){
      steps {
        sh "npm install"
      }
    }
    stage('Test React'){
      steps{
        sh "npm test"
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
        timeout(time: 10, unit: 'MINUTES'){
          waitForQualityGate abortPipeline: true
        }
      }
    }
    
    
  //   stage('Checkout mvn') {
  //       steps {
  //            git branch: 'main', url: 'https://github.com/KSPDeveloper/lbg-hello-world-maven.git'
  //            }
  //       }
  //       stage('Compile') {
  //        steps {
  //            sh "mvn clean compile"
  //       }
  //   }
  //   stage('Test'){
  //       steps{
  //            sh "mvn test"
  //        }
  //   }
  //   stage('Package'){
  //        steps{
  //            sh "mvn -Dmaven.test.skip package"
  //         }
  //     }
  //   stage('SonarQube Analysis for Mvn') 
  //   {
  //   environment {
  //      scannerHome = tool 'sonarqube'
  //   }
  //     steps {
  //   withSonarQubeEnv('sonar-qube-kyle') {
  //     sh "mvn clean verify sonar:sonar"
  //       }
  // }
  // }

  
 }

 
}

