pipeline {
    agent any
    stages {
        stage('Compilar') {
            steps {
                sh 'java -version'
                sh 'mvn -version'
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
        stage('Publicar artefacto') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
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
