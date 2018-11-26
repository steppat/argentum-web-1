pipeline {
    agent any

    environment {
        CC = 'JAVA'
        SERVER = 'TOMCAT'
        JAVA_HOME="${tool 'JDK8'}"
        PATH="${env.JAVA_HOME}/bin:${env.PATH}"
        env.MVN_Home = tool 'M3'
        env.MVN_CMD = "${env.MVN_Home}/bin/mvn"
    }

    //generate token http://localhost:8080/user/admin/configure
    //curl -X POST --user admin:1143d43ca574ab398332d01b0b5ad817d5 -F 'APP=argentum-web' http://localhost:8080/job/argentum-web/buildWithParameters
    //no cli
    //ssh -i key_id_jenkins -l admin -p 5000 localhost build argentum-web

    parameters {
        string(name: 'APP', defaultValue: 'Argentum', description: 'Aplicação Argentum Web')
    }

    stages {

        stage("environment") {
            steps {

              sh 'java -version'
              sh "${env.MVN_CMD} -v"

              echo "Rodando ${env.BUILD_ID} on ${env.JENKINS_URL}"
              echo "Projeto ${params.APP}, Linguagem ${env.CC} on server ${env.SERVER}"
              echo "Branch ${env.BRANCH_NAME}"
              echo "${currentBuild.result}"
            }
        }

        stage('Build') {
            steps {
                echo 'Building...'
                echo "RUNNING MAVEN BUILD"
                sh "${env.MVN_CMD} clean package"
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
            echo "This will always run ${currentBuild.result}"
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
