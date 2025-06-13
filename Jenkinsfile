pipeline {
    agent any
    environment {
        JAVA_HOME = '/root/.sdkman/candidates/java/current'
        PATH = "${env.JAVA_HOME}/bin:${env.PATH}"
    }
    stages {
        stage('Compilar') {
            steps {
                sh 'java -version'
                sh '/root/.sdkman/candidates/maven/current/bin/mvn -version'
                sh '/root/.sdkman/candidates/maven/current/bin/mvn clean compile'
            }
        }
        stage('Probar') {
            steps {
                sh '/root/.sdkman/candidates/maven/current/bin/mvn test'
            }
        }
        stage('Empaquetar') {
            steps {
                sh '/root/.sdkman/candidates/maven/current/bin/mvn package'
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
