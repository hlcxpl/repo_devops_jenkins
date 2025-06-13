pipeline {
    agent any
    tools {
        maven 'maven'     // Usa el nombre configurado en Global Tool Configuration
        jdk 'jdk21'       // Ruta: /root/.sdkman/candidates/java/current
    }
    stages {
        stage('Clonar') {
            steps {
                git url: 'https://github.com/hlcxpl/repo_devops_jenkins.git'
            }
        }
        stage('Compilar') {
            steps {
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
