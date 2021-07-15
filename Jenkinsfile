pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('Checkout'){
            steps {
                git branch: 'jenkins-pipeline-poc', url: 'https://github.com/ramblingbiped/jgsu-spring-petclinic'
            }
        }
        stage('Build'){
            steps {
                sh './mvnw clean package'
            }
            post {
                always {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}