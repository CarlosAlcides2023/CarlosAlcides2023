pipeline {
    agent any
    
    stages {
        stage('Desplegar App') {
            steps {
                script {
                    // Desplegar el contenedor de la aplicación
                    //sh 'docker run -d --name mi_app <nombre_del_contenedor_app>'
                  sh 'docker run -d --name hello-world'
                }
            }
        }
        stage('Ejecutar Pruebas') {
            steps {
                script {
                    // Desplegar el contenedor con pytest
                    //sh 'docker run --rm --name pytest_container --link mi_app:app <nombre_del_contenedor_pytest>'
                  sh 'docker run --rm --name pytest_container --link test-hello-worldlocal'
                }
            }
        }
    }
    
    post {
        always {
            // Limpieza: Detener y eliminar los contenedores después de las pruebas
            sh 'docker stop mi_app || true'
            sh 'docker rm mi_app || true'
            sh 'docker stop pytest_container || true'
            sh 'docker rm pytest_container || true'
        }
    }
}
