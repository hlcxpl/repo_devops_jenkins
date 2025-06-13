pipeline {
    agent any
    environment {
        JAVA_HOME = '/root/.sdkman/candidates/java/current'
        MAVEN_HOME = '/root/.sdkman/candidates/maven/current'
        PATH = "${env.JAVA_HOME}/bin:${env.MAVEN_HOME}/bin:${env.PATH}"
    }
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
