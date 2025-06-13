pipeline {
    agent any
    environment {
        JAVA_HOME = '/root/.sdkman/candidates/java/current'
        PATH = "${env.JAVA_HOME}/bin:${env.PATH}"
    }
    tools {
        maven 'maven'
    }
    stages {
        stage('Compilar') {
            steps {
                sh 'java -version'
                sh 'mvn clean compile'
            }
        }
        stage('Probar') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Empaquetar') {
            steps {
                sh 'mvn package'
            }
        }
    }
    post {
        success {
            echo '🎉 El build fue exitoso'
        }
        failure {
            echo '💥 El build falló'
        }
    }
}
