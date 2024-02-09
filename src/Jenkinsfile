/*pipeline{
    agent any
    stages{
        satage('docker build'){
            steps{
                script{
                    sh"docker nuild -f pipelin/Dockerfile -t laboratorio:1.0.0-${BUILD_ID} pipelin/Dockerfile"
                }
            }
        }
        satage('docker push'){
            steps{
                script{
                    sh"docker push pipelin/Dockerfile:1.0.0-${BUILD_ID}"
                }
            }
        }
    }       
}*/
//La libreria que vamos a utilizar
@Library('jenkinsfile-shared-library') _       

/* definimos la variable config que se trata de un yaml que
leemos directamente del fichero, aqui se pueden definir
nuevas variables que se enviar a pipelineToChoose y asi
poder decidir entre otros pipelines */                          
def config = readYaml text: """                       
---                       
  APP_TYPE: 'test'                       
"""

//creamos el map env                                              
config.keySet().each{                       
    env."${it}" = config[it]                       
}       

//invocamos el pipeline que nos devuelve el que ejecutaremos                                       
def pipelineToRun = pipelineToChoose(env)       
                                       
echo """                       
Pipeline Running: ${pipelineToRun}                      
"""       

//Se ejecuta                
"${pipelineToRun}"()