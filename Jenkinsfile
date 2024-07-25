pipeline {
    agent any
    tools{
        maven 'MAVEN3.9.8'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/mtaori/variable.git', branch: 'Development'
            }
        }

        stage('Build') {
            steps {
                script {
                    echo "Building pull request branch Development"
                    sh 'mvn clean install'   
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo "Running tests on pull request branch Development"
                    
                    sh 'mvn test'
                    
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Pipeline succeeded.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}   
