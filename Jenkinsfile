pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/agm72/JenkinsDependencyCheckTest.git'
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
