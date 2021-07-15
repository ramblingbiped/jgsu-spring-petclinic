pipeline {
    agent any
    triggers {
        cron('* * * * *')
    }
    stages {
        stage('Checkout'){
            steps {
                git branch: 'jenkins-pipeline-poc', url: 'https://github.com/ramblingbiped/jgsu-spring-petclinic.git'
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