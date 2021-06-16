//Este archivo lo usa el pipeline de jenkins  
pipeline {
    agent {
        label 'brian' 
    }

        stages {
        stage("Comprobando funcionamiento de jenkins"){
                steps {
                    script {			
                        sh "echo \"Current workspace is $WORKSPACE\""
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
        	            cd dist
                        cd Frontend
                        mv * /var/www/html'''
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
