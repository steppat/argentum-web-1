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
                echo "Branch ${env.BRANCH_NAME}"
                echo "${currentBuild.result}"
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
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
