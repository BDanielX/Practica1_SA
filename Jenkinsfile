//Este archivo lo usa el pipeline de jenkins  
pipeline {
    agent {
        label 'master' 
    }

        stages {
        stage("Comprobando funcionamiento de jenkins"){
                steps {
                    script {			
                        sh "echo 'Estoy en el stage 1'"
                    }
                }   
            }

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
	
	stage("Realizo build"){
                steps {
                    script {			
                        sh '''cd Frontend
	                ng build
        	        http-server ./dist/Frontend'''
                    }
                }   
            }
    }

    post { 
        always {          
            deleteDir()
            sh "echo 'Entra en always'"
        }
        success {
            sh "echo 'Entra en success'"
        }
        failure {
            sh "echo 'Entra en failure'"
        }   
    }
}
