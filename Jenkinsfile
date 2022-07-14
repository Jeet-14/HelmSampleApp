pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/Jeet-14/HelmSampleApp.git'

                // Run Maven on a Unix agent.
                sh "helm version"
                
                //listing files
                sh "ls -la"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    echo "Helm chart deployed"
                }
            }
        }
    }
}
