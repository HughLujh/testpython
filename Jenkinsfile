pipeline { 
    agent any 

    stages { 
        stage('Download'){ 
            steps{ 
                echo "downloading data" 
                git branch: 'main', credentialsId: '1', url: 'https://github.com/HughLujh/testpython.git'
            } 
        } 

        stage('Install Snyk') {
            steps {
                sh """npm install -g snyk"""
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
                    sh """python3 assembler.py"""
                    sh """chmod +x assembler.py"""
                    sh """snyk test --file=requirements.txt"""  // Assuming requirements.txt lists the dependencies
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
