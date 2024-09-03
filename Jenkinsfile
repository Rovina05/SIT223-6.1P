pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                echo 'Tool used: Maven '
                
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
                echo 'Tools used: JUnit, TestNG'
                
            }
            post {
                always {
                    script {
                        emailext(
                            to: 'loborovina45@gmail.com',
                            subject: "Unit and Integration Tests Completed: ${currentBuild.fullDisplayName}",
                            body: """
                                The Unit and Integration Tests stage has completed with status: ${currentBuild.currentResult}.
                                Please check Jenkins for detailed logs.
                            """,
                            attachLog: true
                        )
                    }
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing Code Analysis...'
                echo 'Tool used: SonarQube'
                
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan...'
                echo 'Tool used: OWASP Dependency Check'
                
            }
            post {
                always {
                    script {
                        emailext(
                            to: 'loborovina45@gmail.com',
                            subject: "Security Scan Completed: ${currentBuild.fullDisplayName}",
                            body: """
                                The Security Scan stage has completed with status: ${currentBuild.currentResult}.
                                Please check Jenkins for detailed logs.
                            """,
                            attachLog: true
                        )
                    }
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                echo 'Tool used: Custom deployment scripts'
                
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging...'
                echo 'Tool used: Custom integration test scripts'
                
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                echo 'Tool used: Custom deployment scripts'
                
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
