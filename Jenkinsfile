pipeline {
 agent any
 environment {
  dotnet = 'C:\\Program Files\\dotnet\\dotnet.exe'
 }
 stages {
  stage('Checkout') {
   steps {
    git url: 'https://github.com/proshailendra/ASPNetCoreApp', branch: 'master'
   }
  }
  stage('Build') {
   steps {
    bat 'dotnet build ASPNETCoreApp.sln --configuration Release'
   }
  }
 }
}
