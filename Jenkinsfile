pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '/usr/local/share/dotnet/dotnet build eShopOnWeb.sln'
      }
    }

    stage('Units') {
      steps {
        sh '/usr/local/share/dotnet/dotnet test     tests/UnitTests'
      }
    }

    stage('Integrations tests') {
      steps {
        sh '''
 /usr/local/share/dotnet/dotnet test     tests/IntegrationTests'''
      }
    }

    stage('Functionals testa') {
      steps {
        sh '/usr/local/share/dotnet/dotnet test     tests/FunctionalTests'
      }
    }

    stage('Deployment') {
      steps {
        sh '/usr/local/share/dotnet/dotnet publish eShopOnWeb.sln -o /var/aspnet'
      }
    }

  }
}