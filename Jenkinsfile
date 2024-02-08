pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'dotnet build eShopOnWeb.sln'
      }
    }

    stage('Tests') {
      parallel {
        stage('Units') {
          steps {
            sh 'dotnet test     tests/UnitTests'
          }
        }

        stage('Inegrations') {
          steps {
            sh 'dotnet test     tests/IntegrationTests'
          }
        }

        stage('Functionnals') {
          steps {
            sh 'dotnet test     tests/FunctionalTests'
          }
        }

      }
    }

    stage('Deployment') {
      steps {
        sh 'dotnet publish eShopOnWeb.sln -o /var/aspnet '
      }
    }

  }
}