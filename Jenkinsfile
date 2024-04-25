pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Clona el repositorio y configura el ambiente
                script {
                    git branch: "${env.CHANGE_BRANCH}", credentialsId: 'luis486', url: "${env.CHANGE_URL}"
                }
            }
        }
        /*
        stage('Unit Tests') {
            steps {
                // Ejecuta las pruebas unitarias
                sh 'tu_comando_de_pruebas_unitarias'
            }
        }
        
        stage('Integration Tests') {
            steps {
                // Puedes agregar una etapa para pruebas de integración si es necesario
                sh 'tu_comando_de_pruebas_de_integracion'
            }
        }
        
        stage('Deploy') {
            steps {
                // Aquí puedes agregar pasos para desplegar la aplicación si las pruebas pasan
                sh 'tu_comando_de_despliegue'
            }
        }**/

        stage('Deploy with kustomize') {
            steps {
                // Ejecuta el customize para lanzar todo el ambiente
                dir('k8s'){
                    sh 'kubectl apply -k .'
                }
                
            }
        }
    }
    
    post {
        success {
            // Si todas las etapas tienen éxito, puedes notificar el resultado
            echo 'Pipeline ejecutado correctamente!'
        }
        failure {
            // Si alguna etapa falla, puedes notificar el resultado
            echo 'Pipeline falló. Revisa los pasos anteriores.'
        }
    }
}
