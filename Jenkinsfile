pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '/usr/local/share/dotnet/dotnet build eShopOnWeb.sln'
      }
    }

    stage('Tests') {
      parallel {
        stage('Units') {
          steps {
            sh '/usr/local/share/dotnet/dotnet test     tests/UnitTests'
          }
        }

        stage('Inegrations') {
          steps {
            sh '/usr/local/share/dotnet/dotnet test     tests/IntegrationTests'
          }
        }

        stage('Functionnals') {
          steps {
            sh '/usr/local/share/dotnet/dotnet test     tests/FunctionalTests'
          }
        }

      }
    }

    stage('Deployment') {
      steps {
        sh '/usr/local/share/dotnet/dotnet publish eShopOnWeb.sln -o /var/aspnet '
      }
    }

  }
}