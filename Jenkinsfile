pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/nasiroddin-qatib/Nexus-CICD/'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh 'mvn sonar:sonar'
                }
            }
        }

        stage('Quality Gate') {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }

        stage('Package') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Nexus') {
            steps {
                sh 'mvn deploy'
            }
        }

        stage('Deploy using Ansible') {
            steps {
                ansiblePlaybook(
                    credentialsId: 'tomcat',
                    disableHostKeyChecking: true,
                    installation: 'ansible',
                    inventory: '/etc/ansible/hosts',
                    playbook: '/etc/ansible/deploy.yml'
                )
            }
        }

    }
}
