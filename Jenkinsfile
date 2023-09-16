pipeline {
    agent { label 'Agent1' }

    stages {
        stage('Download'){ 
            steps{ 
                echo "downloading data" 
                git branch: 'main', credentialsId: 'e4020932-a0c4-430c-9a84-4545ed7eb723', url: 'https://github.com/HughLujh/testpython.git'
            } 
        } 

        stage('Test') { 
            steps { 
                dir('testProject') { 
                    echo 'Testing...' 
                    script {
                        // 获取所有.py文件
                        def pyFiles = fileTree(dir: '.', include: '**/*.py')
                        pyFiles.each { pyFile ->
                            snykSecurity targetFile: pyFile, snykInstallation: 'Snyk Security', snykTokenId: 'd67e5a54-9b89-4c65-b2d6-cd788769dd3a'
                        }
                    }
                } 
            }
        }
    }
}
