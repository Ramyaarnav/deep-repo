pipeline {
    agent {
        label 'ubu'
    }

    stages {
        stage('Code Checkout') {
            steps {
                sh "echo 'Checkout Completed'"
                sh 'apt install python3 -y'
            }
        }
        stage('Build') {
            steps {
                sh "echo 'Build Completed'"
                sh 'python3 automation.py'
            }
        }
    }
    post {
        always {
            mail to: 'cham.deepika@gmail.com',
                 subject: "Jenkins Build Notification: ${currentBuild.fullDisplayName}",
                 body: """\
                 Build Status: ${currentBuild.currentResult}
                 Project: ${env.JOB_NAME}
                 Build Number: ${env.BUILD_NUMBER}
                 Build URL: ${env.BUILD_URL}
                 """
        }
    }
}

