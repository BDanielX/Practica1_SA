//Este archivo lo usa el pipeline de jenkins  
//import groovy.json.JsonSlurperClassic

//def jsonParse(def json) {
//    new groovy.json.JsonSlurperClassic().parseText(json)
//}

pipeline {
    agent {
        label 'master' 
    }
    environment {
        appName = "variable" 
    }
    stages {
        stage("paso 1"){
            steps {
                script {			
                    sh "echo 'hola mundo'"
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
