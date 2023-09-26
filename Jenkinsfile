pipeline {
    agent any
    stages {
        stage('Desplegar App') {
            steps {
                script {
                    // Desplegar el contenedor de la aplicación
                    //sh 'docker run -d --name mi_app <nombre_del_contenedor_app>'
                  sh 'docker run -d -p 5000:5000 --name aplicacion2 hello-world'
                }
            }
        }
        stage('Ejecutar Pruebas') {
            steps {
                script {
                    // Desplegar el contenedor con pytest
                    //sh 'docker run --rm --name pytest_container --link mi_app:app <nombre_del_contenedor_pytest>'
                  sh 'docker run -d --name test2 test-hello-worldlocal'
                }
            }
        }
    }
    
    post {
        always {
            // Limpieza: Detener y eliminar los contenedores después de las pruebas
            sh 'docker stop aplicacion2 || true'
            sh 'docker rm aplicacion2 || true'
            sh 'docker stop test2 || true'
            sh 'docker rm test2 || true'
        }
    }
}
