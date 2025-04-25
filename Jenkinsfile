pipeline {
    agent { label 'agent2' }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/JUANPLATAPOLANIA/Pythonn.git'
            }
        }
        stage('Test') {
            steps {
                // Ejecuta pytest y genera reporte JUnit
                sh 'pytest --maxfail=1 --disable-warnings -q --junitxml=results.xml'
            }
        }
    }

    post {
        always {
            // Publica el reporte en la interfaz de Jenkins
            junit 'results.xml'
        }
    }
}