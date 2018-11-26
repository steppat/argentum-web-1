pipeline {
    agent any

    environment { 
        CC = 'JAVA'
        SERVER = 'TOMCAT'
    }
    
    parameters {
        string(name: 'APP', defaultValue: 'Argentum', description: 'Aplicação Argentum Web')
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                echo "Rodando ${env.BUILD_ID} on ${env.JENKINS_URL}"
                echo "Projeto ${params.APP}, Linguagem ${env.CC} on server ${env.SERVER}"

            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
