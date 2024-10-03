pipeline {
    agent any

    stages {
        stage('Run Shell Script') {
            steps {
                // Run the shell script
                sh './hello.sh'
            }
        }
    }

    post {
        always {
            // Clean up workspace after build
            cleanWs()
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}

