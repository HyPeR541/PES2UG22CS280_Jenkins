pipeline {
    agent any
    
    stages {
        stage('Initialize') {
            steps {
                script {
                    sh 'echo "#include <iostream>\nint main() { std::cout << \"Hello, Jenkins!\" << std::endl; return 0; }" > program.cpp'
                }
            }
        }
        
        stage('Build') {
            steps {
                script {
                    sh 'g++ program.cpp -o PES2UG22CS280-1'
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    sh './PES2UG22CS280-1'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    sh 'git init'
                    sh 'git add program.cpp'
                    sh 'git commit -m "Added new C++ file"'
                    sh 'git remote add origin YOUR_GIT_REPOSITORY_URL'
                    sh 'git push -u origin main'
                }
            }
        }
    }
    
    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}
