pipeline {
    agent docker
    stages {
        stage('Build') {
            steps {
                echo "Building using Maven..."
                // Maven could be invoked here
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running tests using JUnit and Selenium..."
                // JUnit and Selenium commands here
            }
            post {
                always {
                    emailext (
                        to: 'mohommadawaze@gmail.com',
                        subject: "Jenkins Build: ${currentBuild.fullDisplayName}",
                        body: """<p>Stage 'Unit and Integration Tests' completed with status ${currentBuild.result}</p>
                                 <p>Check console output at ${env.BUILD_URL} to view the results.</p>""",
                        attachLog: true
                    )
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Analyzing code with SonarQube..."
                // SonarQube integration here
            }
        }
        stage('Security Scan') {
            steps {
                echo "Conducting security scan with OWASP ZAP..."
                // OWASP ZAP commands here
            }
            post {
                always {
                    emailext (
                        to: 'mohommadawaze@gmail.com',
                        subject: "Jenkins Build: ${currentBuild.fullDisplayName}",
                        body: """<p>Stage 'Security Scan' completed with status ${currentBuild.result}</p>
                                 <p>Check console output at ${env.BUILD_URL} to view the results.</p>""",
                        attachLog: true
                    )
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying to AWS EC2 Staging..."
                // AWS CLI commands to deploy
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests in staging environment..."
                // Testing commands here
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying to AWS EC2 Production..."
                // AWS CLI commands to deploy
            }
        }
    }
}
