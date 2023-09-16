pipeline { 
    agent any 

    stages { 
        stage('Install Node.js and npm') {
            steps {
                sh """
                    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
                    export NVM_DIR="$HOME/.nvm"
                    [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
                    nvm install 14  # Install Node.js 14
                """
            }
        }

        stage('Download'){ 
            steps{ 
                echo "downloading data" 
                git branch: 'main', credentialsId: '1', url: 'https://github.com/HughLujh/testpython.git'
            } 
        } 

        stage('Install Snyk') {
            steps {
                sh """ 
                    npm install -g snyk
                """
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
