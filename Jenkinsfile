pipeline {
    agent any
    environment {
        // Define la versión de Node.js que usarás, si es necesario.
        NODE_VERSION = '18'
    }
    stages {
        stage('Checkout') {
            steps {
                // Si el repositorio es público y el Jenkinsfile está en la raíz, se puede usar checkout scm:
                checkout scm
                // Si prefieres especificar el repositorio y rama, y agregar credenciales si es privado, puedes usar:
                /*
                git url: 'https://github.com/SHuanca01/repo-CI.git',
                    branch: 'main',
                    // Descomenta la siguiente línea y reemplaza 'github-token' por el ID de la credencial almacenada en Jenkins, si el repo es privado.
                    // credentialsId: 'github-token'
                */
            }
        }
        stage('Build') {
            steps {
                echo "Instalando dependencias..."
                // En Windows, usa el comando bat en lugar de sh.
                bat 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo "Ejecutando pruebas..."
                bat 'npm test'
            }
        }
        stage('Deploy') {
            steps {
                echo "Desplegando aplicación..."
                // Puedes iniciar la aplicación en segundo plano o como se requiera.
                bat 'npm start'
            }
        }
    }
    post {
        success {
            echo "✅ Pipeline completado con éxito"
        }
        failure {
            echo "❌ El pipeline ha fallado"
        }
    }
}
