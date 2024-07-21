pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                git credentialsId: '04d7922f-bcb9-4729-8b34-e83f2a20c0c3', branch: 'master', url: 'https://github.com/agm72/JenkinsDependencyCheckTest.git'
            }
        }

        stage('OWASP DependencyCheck') {
            steps {
                dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
            }
        }
    }   
    post {
        success {
            dependencyCheckPublisher pattern: 'dependency-check-report.xml'
        }
    }
}
