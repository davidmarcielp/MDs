pipeline {
    agent any // Se utilizará para la mayoria de steps un agente any.
    
    
    stage('Initialize Repository Configuration') {
        steps {
            script {
                /**
                Descripcion: En esta fase se realizan las siguientes acciones:
                Si existe el archivo hugo/generate_new_hugo_version, se obtiene su contenido como nombre de versión y se carga la rama master del repositorio.
                Si no existe el archivo hugo/generate_new_hugo_version, se marca una variable para saltar el resto de pasos.
                */ 
                env.WORKSPACE = pwd()
                echo "env.WORKSPACE " + env.WORKSPACE
            }
        }
    }
}