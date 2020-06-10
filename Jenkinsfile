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
  stage('Build and Publish') {
   steps {
    bat 'dotnet publish ASPNETCoreApp.sln --configuration Release'
   }
  }
  stage('Test: Unit Test'){
   steps {
     bat "dotnet test ASPNETCoreAppUnitTest\\ASPNETCoreAppUnitTest.csproj"
     }
  }
  stage('Azure Deployment') {
     steps {
       azureWebAppPublish azureCredentialsId: env.AZURE_CRED_ID,resourceGroup: env.RES_GROUP, appName: env.WEB_APP, sourceDirectory: "ASPNETCoreApp/bin/Release/netcoreapp3.1/publish/"
      }
    }
 }
}
