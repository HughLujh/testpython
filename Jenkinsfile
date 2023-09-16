pipeline { 

  agent any 

  stages { 

        stage('Download'){ 

            steps{ 

                echo "downloading data" 
                git branch: 'main', credentialsId: '1', url: 'https://github.com/HughLujh/testpython.git'
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
                sh """ls"""
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