/*
* El siguiente JenkinsFile se corresponde al Job 1 Correspondiente a la Recoleccion de APIs
* de la solución MMPORTAL
*/
class APIChanges {
    /*
    *   La clase APIChanges se encarga de las siguientes tareas:
    *   - Comprobar si para una serie de rutas, estas contienen una API valida
    *   - Almacenar dichas rutas para una comprobación posterior.
    *   - Almacenar el json que contiene la información relativa al commit de cabecera "head_commit"
    */

	private def validExtensions = ["yaml","md"] // Array que contiene las extensiones validas para las rutas
    private int NumberAPIsAffected; // Contador del numbeo de APIs afectadas en la ejecucion del Job
    private boolean APIChanged = false /*
                                        * true -> Indica que hay APIs modificadas en este Job
                                        * false -> (Por defecto), indica que en el job actual no existen APIs modificadas o anadidas
    */
    private String head_commit = "" // String que albergará el identificador del commit de cabecera

    def APIsRoutes = []; // Array de String que almacenará las rutas modificadas o anadidas
    
    def getHeadCommit() {
        /*
        * Devuelve el identificador del commit de cabecera
        */
        return head_commit;
    }
    
    def setHeadCommit(commitId) {
        /*
        * Establece el identificador del commit de cabecera
        */
        head_commit = commitId
    }

    def getNumberAPIsAffected() {
        /*
        * Devuelve el número de APIs afectadas
        */
        return NumberAPIsAffected;
    }
    
    def checkIsAPI(route){
        /*
        *   Input : route -> String con la ruta a comprobar, si es una ruta de API valida
        *   Output: isRouteAPI-> Booleano
        *                   true -> Indica que la ruta actual es una API.
        *                   false -> Indica que la ruta actual no es una API.
        *   Descripcion: Este metodo se encarga de comprobar si una ruta es una API valida.
        *   En primer lugar se obtiene la extension del fichero, si la extension está en el array de extensiones validas
        *   se comprueba con una expresión regular si presenta el siguiente patrón "/doc/swagger.yaml" en caso afirmativo se considera una 
        *   ruta de API.
        */
        boolean isRouteAPI = false;
		String extension = route.tokenize(".")[-1];
		if(extension in validExtensions) {
		    // Check is a valid folder by now only check if doc/ is present
			if(route =~/(.*)doc\/swagger.yaml/){
                
			    isRouteAPI = true;    
			}
            if(route =~/(.*)doc\/(.*).md/){
                
			    isRouteAPI = true;    
			}
		}
        return isRouteAPI;
    }
    
    def computeAPIChanged() {
        /*
        *   Descripcion: Este metodo interno actualiza el booleano APIChanged, mediante la comprobación del numero actual de APIs almacenadas
        *   Si este numero es mayor que cero el booleano APIChanged cambia su valor a true, en caso contrario se pone a false.
        *
        */
        int total_size_changes = this.getNumberAPIsAffected()
	    if( total_size_changes > 0)
	    {
	        this.APIChanged = true
        } else {
            this.APIChanged = false
        }
    }

    def setAPIsRoutes(arrayCommits) {
        /*
        *   Input : arrayCommits -> Array con las rutas de cada uno de los commits afectados.
        *   
        *   Descripcion: Este metodo itera sobre cada una de las rutas, y tras comprobar si es una API, la añade al arry APIsRoutes, 
        *   si y solo si esa ruta no estaba añadida antes.
        *   Tras acabar, se setea el valor de NumberAPIsAffected a partir del tamano actual de APIsRoutes
        *   y se llama a computeAPIChanged()  para actualizar el valor del booleano APIChanged.
        *
        */
        for(String route in arrayCommits){
			if(checkIsAPI(route)) {
              def alreadyExists = route in APIsRoutes
              if(!alreadyExists){
                    APIsRoutes.add(route)
                }
				
			}
        }
        NumberAPIsAffected = APIsRoutes.size();    
        this.computeAPIChanged()
    }
    
    def getAPIsRoutes() {
        /*
        * Devuelve una copia del array APIsRoutes que contiene las rutas de las APIs
        */
        return APIsRoutes
    }
    
    def getAPIsRoutesToString() {
        /*
        *   Output: routes -> String unico, que contiene las rutas de cada una de las APIs concatenadas y separadas por una nueva linea
        *   Descripcion: Este metodo recorre el array APIsRoutes y devuelve las rutas en ese array en un unico string separadas por nueva linea
        *   El motivo de este metodo es que es necesaria esta representacion de las rutas para trabajar con ellas a nivel de script BASH.d
        */
        //Returns the routes in the following format route1\nroute2..
        String routes = ""
        int routeSize = APIsRoutes.size()
        for(int i=0; i<routeSize;i++) {
            String storedRoute = APIsRoutes[i]
            if(i==routeSize-1){
             routes += storedRoute   
            } else {
                routes += storedRoute+"\n"
            }
            
        }
        
        return routes
    }

    def isAPIChanged() {
        // Devuelve APIChanged, si existe al menos una API en este job el valor de este booleano sera true.
        return APIChanged
    }
    
}


def compute_API_affected(current_commit)
{
    /*
    *   Input: current_commit -> JSON que se corresponde al head_commit o commit de cabecera, valor correspondiente al payload enviado 
    *                           desde el commit de cabecera. 
    *   Output: innerAPIChanges -> Objeto del tipo APIChanges y creado en este metodo, con los valores del commit de cabecera ya incluidos.
    *   Descripcion: Esta funcion( no metodo dado que no pertenece a ninguna clase)
    *    crea el objeto APIChanges que se usará a lo largo del Job, y lo inicializa con los valores del commit de cabecera, en concreto:
    *       - Envia al objeto APIChanges el id del commit de cabecera.
    *       - Envia al objeto APIChanges las rutas de los ficheros anadidos en el commit actual.
    *       - Envia al objeto APIChanges las rutas de los ficheros modificados en el commit actual.
    */
    def added_files = current_commit.added
	def modified_files = current_commit.modified
	APIChanges innerAPIChanges = new APIChanges();
    innerAPIChanges.setHeadCommit(current_commit.id)
	innerAPIChanges.setAPIsRoutes(added_files);
	innerAPIChanges.setAPIsRoutes(modified_files);
	return  innerAPIChanges
}


APIChanges myAPIChanges = new APIChanges() // Se crea el objeto myAPIChanges fuera de la directiva de pipeline, con el objetivo de tener acceso al objeto desde todas las fases.
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

    	            //def payload = readJSON text: env.payload
    	            //def head_commit = payload.head_commit
                    //myAPIChanges =compute_API_affected(head_commit)
                    
                    // La siguiente sentencia establece un bloque en el que el valor de HEAD COMMIT es modificado por el identificador almacenado
                    // Tambien se accede al script bash con las credenciales indicadas anteriormente
    	            
                    //withEnv(["HEAD_COMMIT="+myAPIChanges.getHeadCommit()]) {

                        withCredentials([usernamePassword(credentialsId: '806bdc4e-af90-4255-83fc-b434c30a6720', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                            sh '''#!/bin/bash
                                COMMIT_FILE=current_commit 

                                echo "commit file $COMMIT_FILE"

                                #touch missing_changes_file
                                
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
                    //}
                }
            }
        }
    }
}