pipeline {
    agent {
            // Se establece como agente unico en todas las fases, widdershins.
		  docker {
                    image 'eu.gcr.io/mm-cloudbuild/widdershins:v1.0.0'
                    registryUrl "https://eu.gcr.io"
                    registryCredentialsId "gcr:mm-cloudbuild"
                }
	}
    environment{
        /* Las variables de environment recogidas aqui, son variables de SOLO LECTURA, cuyo acceso es posible desde cada una de las fases.
        * Es posible no obstante con el valor withEnv modificar PARA una fase en concreto el valor de alguna de las variables aqui presentadas 
        */
        ROUTE_LIST = myAPIChanges.getAPIsRoutesToString() // Tiene la lista actual de rutas en formato String
        REPOSITORY = 'https://github.com/masmovil/developer-portal' // Direccion del repositorio
        CREDENTIALS = 'developer-portal' // Credenciales de acceso al repositorio
        BRANCH = 'documentation' // Rama de trabajo
        MAIN_BRANCH = 'master' // Rama principal del trabajo
        UPLOAD = 'github.com/masmovil/developer-portal' // Direccion del repositorio
        HEAD_COMMIT = '' // String con el identificador del HEAD_COMMIT
    }

    stages {
        stage('Webhook Called'){
            /* Comprobamos el commit de cabecera*/
            steps {
    	       	script {
                    /* 
                    Descripcion: En esta fase se realizan las siguientes acciones:
                    1. Se lee en primer lugar el payload enviado desde el hook y recogido en la variable env.payload.
                    2. Se almacena el commit de cabecera y se crea el objeto APIChanges con estos valores (modificando el objeto myAPIChanges)
                    ---- Script Bash
                    3. Se inicializa el repositorio, y se obtiene la lista de commits de la rama master
                    3.1 Si no existe el fichero current_commit, se toma como ultimo commit comprobado el anotado por la variable de git HEAD.
                    3.2 Si existe el fichero current_commit se toma como ultimo commit comprobado el que viene en ese fichero.
                    3.3 Se obtienen los identificadores de los commits restantes comprendidos entre el ultimo de la rama master y el ultimo comprobado.
                        El resultado se guarda en un fichero (missing_commits_file)
                    3.4 Sobre el fichero obtenido en el paso anterior, se obtienen las rutas que afectaban a dicho commit, y se guardan en el fichero missing_changes_file
                    3.5 Se almacena el commit ultimo comprobado en el fichero current_commit.
                    -----
                    4.1 Se comprueba si en el paso anterio se ha creado el fichero missing_changes_file, si es asi se lee, almacenandolo en la variable missing_commits
                    4.2 Si existia el fichero, se añade la informacion de las rutas al objeto myAPIChanges.
                    5. Si no existe información de rutas en myAPIChanges se imprime un mensaje indicando que no existen rutas afectadas en la ejecución de este Job.
                    */
    	            def payload = readJSON text: env.payload
    	            def head_commit = payload.head_commit
                    myAPIChanges =compute_API_affected(head_commit)
                    // La siguiente sentencia establece un bloque en el que el valor de HEAD COMMIT es modificado por el identificador almacenado
                    // Tambien se accede al script bash con las credenciales indicadas anteriormente
    	            withEnv(["HEAD_COMMIT="+myAPIChanges.getHeadCommit()]) {
    	            withCredentials([usernamePassword(credentialsId: '806bdc4e-af90-4255-83fc-b434c30a6720', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                        sh '''#!/bin/bash
                            COMMIT_FILE=current_commit 

                            touch missing_changes_file
                            git init
                            git remote set-url origin "https://${USERNAME}:${PASSWORD}@$UPLOAD"
                            
				            git fetch origin $MAIN_BRANCH
				            
                            if [[ ! -f "$COMMIT_FILE" ]]; then
                                echo "There is no previous commit registered, take HEAD instead"
                                git rev-parse HEAD > current_commit
                            fi
                            
                            var_current_commit=$(cat current_commit)
                            echo "current commit $var_current_commit"
                            echo "head commit $HEAD_COMMIT"
				            
                            git rev-list $var_current_commit..$HEAD_COMMIT > missing_commits_file
				            
                            cat missing_commits_file | while read line; do
				                echo "COMMIT : "+$line
				                echo "-----------------------------------"
				                git diff-tree --no-commit-id --name-only -r $line >> missing_changes_file
				            done
				            
                            echo "Updating current commit with last commit fetched"
                            
                            echo $HEAD_COMMIT > current_commit
                            
                        '''
    	            }
                }
                    // Turn the file into a valid array
                    def missing_commits = readFile(file: 'missing_changes_file').split('\n')
                    if(missing_commits.length > 0 ){
                        if(missing_commits[0] != ""){
                            myAPIChanges.setAPIsRoutes(missing_commits)
                        }
                    }

                if(!myAPIChanges.isAPIChanged()) {
                    echo "There are no API definitions changed in this commit job"
                }
                
	        }
        }
        }
    }
}