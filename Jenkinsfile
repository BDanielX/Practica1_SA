//Este archivo lo usa el pipeline de jenkins  

pipeline {
    agent {
        label 'master' 
    }

    stages {

        stage("Actualizar paquetes"){
            steps {
                script {	
		    sh '''cd Frontend
                    npm install'''
                }
            }   
        }

        stage("Ejecutar pruebas unitarias"){
            steps {
                script {	
		    sh '''cd Frontend
                    ng test --watch=false --browsers=ChromeHeadless'''
                }
            }   
        }
    }

    //El apartado post se ejecuta siempre al terminar los stages
    post {
        //Always se ejecuta siempre que terminan los stages, sin importar el estado 
        always {          
            deleteDir()
            sh "echo 'fase always'"
        }
        //Sucess se ejecuta si se ejecuto todo con exito
        success {
            sh "echo 'fase success'"
        }
        //Failure se ejecuta si hubo alguna falla
        failure {
            sh "echo 'fase failure'"
        }   
    }
}
