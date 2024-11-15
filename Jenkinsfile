pipeline{
    agent any

    stages{
        stage('Checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/Dzhantov/StudentRegistryAppCICD.git'
            }
        }
        stage('Install dependencies'){
            steps{
                script{
                    bat 'npm install'
                }
            }
        }
        stage('Start app and run tests'){
            steps{
                script{
                    bat 'npm start &'
                    bat 'wait-on http://localhost:8080'
                    bat 'npm test'
                }
            }
        }
    }

    post {
        always{
            echo "CI pipeline completed"
        }
    }
}