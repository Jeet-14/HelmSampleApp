pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                
              git branch: 'main',
                credentialsId: 'gitcreds',
                url: 'https://github.com/Jeet-14/HelmSampleApp.git'
        }
    }
        
    stage('Helm Version check')
    {
        steps{
             sh "helm version"
        }
    }
        
     stage('Helm Lint')
    {
        steps{
             sh "helm template nginxapplication ./nginxapp"
        }
    }
        
     stage('Helm Depoly')
    {
        steps{
            withCredentials([file(credentialsId: 'kubeconfig', variable: 'KUBECRED')]) {
    
              sh "helm install nginxapplication ./nginxapp --kubeconfig $KUBECRED "
                 
             }
        }
    }
        
  }
    
}
