pipeline {
    agent any

    tools {
        maven 'MavenTool' // Ensure this Maven tool is configured in Jenkins Global Tools
    }

    stages {
        stage('Print Name') {
            steps {
                sh 'echo "Mahesh"' // Use single quotes around shell command
            }
        }
        stage('Git checkout'){
            steps{
                git(
                    branch: 'main',
                    url: 'https://github.com/msabale001/myrepo.git',
                    credentialsId: 'github-cred'
                    )
            }
        }
    }

    post {
        success {
            emailext(
                to: 'maheshsabale001@gmail.com',
                subject: "The build is #${BUILD_NUMBER}",
                body: '''
                <p>The build was <b>Successful</b></p>
                ''',
                mimeType: 'text/html'
            )
        }
        always{
            cleanWs()
        }
    }
}
