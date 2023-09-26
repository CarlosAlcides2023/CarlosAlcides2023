pipeline {
    agent any
    stages {
        stage('Desplegar App') {
            steps {
                script {
                    // Desplegar el contenedor de la aplicación
                    //sh 'docker run -d --name mi_app <nombre_del_contenedor_app>'
                  sh 'docker run -d --name aplicacion1 hello-world'
                }
            }
        }
        stage('Ejecutar Pruebas') {
            steps {
                script {
                    // Desplegar el contenedor con pytest
                    //sh 'docker run --rm --name pytest_container --link mi_app:app <nombre_del_contenedor_pytest>'
                  sh 'docker run -d --name test test-hello-worldlocal'
                }
            }
        }
    }
    
    post {
        always {
            // Limpieza: Detener y eliminar los contenedores después de las pruebas
            sh 'docker stop hello-world || true'
            sh 'docker rm hello-world || true'
            sh 'docker stop test-hello-worldlocal || true'
            sh 'docker rm test-hello-worldlocal || true'
        }
    }
}
