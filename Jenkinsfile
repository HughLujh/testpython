pipeline { 

  agent any 

  stages { 

        stage('Download'){ 

            steps{ 

                echo "downloading data" 

                git branch: 'main', credentialsId: '5b196ed6-0030-442c-8b30-9f5a5ce97f14', url: 'https://github.cs.adelaide.edu.au/SEP-CD/CD1.git' 

            } 

        } 

        stage('Build') { 

        steps { 

            echo 'Building...' 

        } 

        } 

        stage('Test') { 

        steps { 

            dir('testProject') { 

                echo 'Testing...' 

                snykSecurity snykInstallation: 'Snyk Security', snykTokenId: 'd67e5a54-9b89-4c65-b2d6-cd788769dd3a'
            } 

        } 

        } 

        stage('Deploy') { 

            steps { 

                echo 'Deploying...' 

            } 

        } 

    } 

} 