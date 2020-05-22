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
                    // La siguiente sentencia establece un bloque en el que el valor de HEAD COMMIT es modificado por el identificador almacenado
                    // Tambien se accede al script bash con las credenciales indicadas anteriormente
    	        
                    withCredentials([usernamePassword(credentialsId: '806bdc4e-af90-4255-83fc-b434c30a6720', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                        sh '''#!/bin/bash
                            COMMIT_FILE=current_commit 

                            echo "commit file $COMMIT_FILE"

                            touch missing_changes_file
                            
                            if [[ ! -f "$COMMIT_FILE" ]]; then
                                echo "There is no previous commit registered, take HEAD instead"
                                git rev-parse HEAD > current_commit
                            fi
                            

                            #if [[ "$COMMIT_FILE" == "current_commit" ]]; then
                            #    var_current_commit=$(git log --format="%H" -n 2)
                            #else
                            #    var_current_commit=$(cat current_commit)
                            #fi

                            var_current_commit=$(cat current_commit)
                            if [[ -z "$var_current_commit" ]]; then
                                var_current_commit=$(git log --format="%H" -n 2)
                            fi

                            echo "current commit $var_current_commit"
                            HEAD_COMMIT=$(git log --format="%H" -n 1)
                            echo $HEAD_COMMIT > head_commit
                            echo "head commit $HEAD_COMMIT"
                            
                            git rev-list $var_current_commit..$HEAD_COMMIT > missing_commits_file
                            #git rev-list $HEAD_COMMIT..$var_current_commit > missing_commits_file
                            
                            cat missing_commits_file | while read line; do
                                echo "COMMIT : "+$line
                                echo "-----------------------------------"
                                git diff-tree --no-commit-id --name-only -r $line >> missing_changes_file
                            done
                            
                            echo "Updating current commit with last commit fetched"
                            
                            echo $HEAD_COMMIT > current_commit
                            
                        '''
                    }

                    env.WORKSPACE = pwd()
                    echo "env.WORKSPACE " + env.WORKSPACE

                    getHeadCommit = fileExists "${env.WORKSPACE}/head_commit"
                    echo "getHeadCommit " + getHeadCommit

                    if(getHeadCommit){                            
                        headCommit = readFile "${env.WORKSPACE}/head_commit"
                        echo "headCommit " + headCommit
                        env.HEAD_COMMIT = headCommit
                    
                        /*git url: REPOSITORY,
                            credentialsId: CREDENTIALS,
                            branch: BRANCH*/
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
        stage('Initialize Repository Configuration') {
            steps {
                script {
                        /*
                        *   Descripcion: 
                        *       Si y solo si hay APIs afectadas:
                        *   1. Se inicializa a traves del plugin de GIT, el repositorio a través de la rama de documentation.
                        ------- Script Bash
                        *   2. Modificando a traves de la directiva withEnv el valor de la variable de entorno HEAD_COMMIT
                        *   2.1 Se actualiza el valor del fichero current_commit, con el valor de la variable HEAD_COMMIT que contiene el identificador del ultimo commit comprobado.
                        *   Nota: Este paso es necesario, puesto que al cambiar a la rama documentation se ha perdido el valor con respecto al paso anterior.
                        */
                        if(myAPIChanges.isAPIChanged()) {
                            // Is neccesary to create BRANCH documentation previously in order to have this job runnging.
                            git url: REPOSITORY,
                                credentialsId: CREDENTIALS,
                                branch: BRANCH
                                                        
        	                //After this, some files are rewritten by the plugin itself, update again the current commit file
                            withEnv(["HEAD_COMMIT="+myAPIChanges.getHeadCommit()]) {
                            
                            sh '''#!/bin/bash
                                echo "Updating current commit with last commit fetched"
                                echo $HEAD_COMMIT > current_commit
                                echo "Last commit after update:"
                                cat current_commit
                            '''
                        }
                    }
                }
            }
        }
        
        stage('Push to Git2') {
            steps {
                script {
                                            /*
                    * Descripcion:
                    *   Si y solo si hay APIs afectadas:
                    * ---------Script bash
                    *  0- Con las credenciales correspondientes
                    *  1. Se establece la url del repositorio remoto
                    *   2. Se establece el usuario y su email
                    * 3. Se realiza un commit con las APIs afectadas.
                    */
                        withCredentials([usernamePassword(credentialsId: '806bdc4e-af90-4255-83fc-b434c30a6720', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                            
                            sh '''#!/bin/bash
                                git remote set-url origin "https://${USERNAME}:${PASSWORD}@$UPLOAD"
                                git config user.email "HUGO AUTOMATED SYSTEM"
                                git config user.name  "HUGO AUTOMATED SYSTEM"
                                
                rm -rf DRAFT/en/docs/REAL_API_doc_swagger MDs/en/docs/REAL_API_doc_swagger

                                #push to documentation branch
                                git add -A
                                git commit -m "HUGO AUTOMATIC COMMIT"
                                git push --set-upstream origin HEAD:documentation
                                echo "Last affected commit:"
                                cat current_commit
                                '''
                        }
                    
                }
            }
        }
    
        
        stage('Checking Last Commit Affected Files') {
            steps {
                script {
                    /*
                    * Descripcion:
                    *   Si y solo si hay APIs afectadas:
                    * ---------Script bash
                    *  0. Se modifica mediante withEnv, el valor de la variable ROUTE_LIST, con el conjunto de rutas de ficheros a descargar
                    *  1. Se inicializa las carpetas temporales de trabajo
                    *  2. Se itera sobre ROUTE_LIST, y para cada ruta.
                    *  2.1 Se hace un checkout de la ruta, desde la rama master a la rama documentacion
                    *  2.2 Se obtiene la version, y se modifica el nombre del fichero que contiene la API
                    *  2.3 Se copia la API a la carpeta temporal files/
                    */
                    if(myAPIChanges.isAPIChanged()){
                        withEnv(["ROUTE_LIST="+myAPIChanges.getAPIsRoutesToString()]) {                                  
                        sh '''#!/bin/bash
                            #init working folders
                            rm -rfv files
                            mkdir files
                            rm -rfv workspace
                            mkdir workspace
                            
                            #copy .yaml s to folder
                            #we get the last commit files
                            #we filter only the onew with the desired format
                            #we iterate them
                            echo 'Print Routes....'
                            echo "$ROUTE_LIST"
                            echo "-----------------------------------"
                            echo "$ROUTE_LIST" | while read line; do
                            
                                echo "line $line"
                                git checkout origin/master -- "$line"
                            
                                echo "Copying line '$line' to files"
                                
                                #replace / with _
                                #remove spaces and set the name as ver.si.on__url_to_file then
                                #copy it to files folder to use it in future steps
                                
                                name=${line////_}
                                name="$(echo -e "${name}" | tr -d '[:space:]')"
                                version=$(cat "${line}" | grep  -m 1 -h version | head -1 )
                                version="$(echo -e "${version}" | tr -d '[:space:]')"
                                version=${version#"version:"}
                                version1="${version%%.*}"
                                
                                name="${version}__${name}"
                                echo "name $name"
                                echo "version $version"
                                echo "version1 $version1"
                                
                                #if the file contains a version
                                #set the file at the right place to be treated
                                if [[ $version1 =~ ^[0-9]+$ ]] ; then
                                    echo "copy file $line"
                                    cp -- "$line" files/$name
                                fi
                                
                                #cp -- "$line" files/$name

                                #remove the file of the checkout
                                #TODO git doesnt take into account empty folders so it wont push the remainings
                                #but this folder would persist in jenkins workspace
                                #we could delete this folder (we should check it is not a folder we are using like DRAFT)
                                rm -rf "$line"
                                
                                echo " "
                            done

                            echo "------"
                            ls files
                            '''
                        }
                    }
                }
            }   
        }
        

        stage('Transformation into Markdown') {
            steps {
                echo 'Calling docker image to transform the APIs into Markdown'
                script {
                                        /*
                    * Descripcion:
                    *   Si y solo si hay APIs afectadas:
                    * ---------Script bash
                    *  1. Se itera para cada fichero que hay en files
                    *  1.1 Se llama a Widdershins para que transforme la API a Markdown, y se almacena en workspace
                    *  2.1 Se hace un checkout de la ruta, desde la rama master a la rama documentacion
                    * TODO : Hay una comprobacion de que existan ficheros en files/, en este caso si se ha llegado a este step es porque deberia haber APIs en ese directorio
                    * TODO: Existe tambien una comprobacion de diferentes extensiones (json / yaml / yml) que ya se ha realizado previamente.
                    */
                    if(myAPIChanges.isAPIChanged()){
                        
                        sh '''#!/bin/bash
                        
                        FILES=files/*
                        echo "<$FILES>"
                        
                        ls -lrt files
                        
                        for f in $FILES
                        do
                        
                            echo "f: $f"
                        
                            if [[ "$f" == "files/*" ]]; then
                        
                                echo "there are no files"
                        
                            else
                        
                                echo "there are file $f"
                        
                                if  [[ $f == *.json ]] ; then
                                    filename="$(basename -- "$f" .json)"
                                    filename="$filename.md"

                                    widdershins --language_tabs 'java:Java' 'go:Go' 'javascript:JavaScript' -o workspace/$filename $f
                                fi
                        
                                if [[ $f == *.yaml ]] ; then
                                    filename="$(basename -- "$f" .yaml)"
                                    filename="$filename.md"

                                    widdershins --language_tabs 'java:Java' 'go:Go' 'javascript:JavaScript' -o workspace/$filename $f
                                fi
                                
                                if [[ $f == *.yml ]] ; then
                                    filename="$(basename -- "$f" .yml)"
                                    filename="$filename.md"

                                    widdershins --language_tabs 'java:Java' 'go:Go' 'javascript:JavaScript' -o workspace/$filename $f
                                fi

                                if [[ $f == *.md ]] ; then
                                    filename="$(basename -- "$f" .md)"
                                    filename="$filename.md"


                                    cp $f workspace/$filename
                                fi
                        
                            fi
                            
                        done
                        
                        rm -rf files/*
                       
                        '''
                    }
                }
            }
        }
            
        stage('Create Parent Folders') {
            steps {
                script {
                    /*
                    * Descripcion:
                    *   Si y solo si hay APIs afectadas:
                    * ---------Script bash
                    *  1. Se crean si no existen las siguientes carpetas
                    *  MDs, DRAFT, PUBLISH
                    */
                    if( myAPIChanges.isAPIChanged()) {
                        sh '''#!/bin/bash
                        
                        MDS_FOLDER="MDs/"
                        if [ ! -d "$MDS_FOLDER" ]; then
                            mkdir $MDS_FOLDER
                        fi
                        DRAFT_FOLDER="DRAFT/"
                        if [ ! -d "$DRAFT_FOLDER" ]; then
                            mkdir $DRAFT_FOLDER
                        fi
                        PUBLISH_FOLDER="PUBLISH/"
                        if [ ! -d "$PUBLISH_FOLDER" ]; then
                            mkdir $PUBLISH_FOLDER
                        fi
                        '''
                    }
                }
            }
        }
        
        stage('Create Subfolders and MDs') {
            steps {
                script {
                    if( myAPIChanges.isAPIChanged()) {
                    /*
                    * Descripcion:
                    *   Si y solo si hay APIs afectadas:
                    * ---------Script bash
                    *  1. Para cada fichero en workspace
                    *  1.1 Se extrae la cabecera y el versionado del fichero,a si como el nombre del mismo
                    *  1.2 Se crea en MDs, PUBLISH, y DRAFT la carpeta dentro de en/docs/ con el nombre de la API sobre la que se esta iterando
                    *  1.3 Se crea _index.md en DRAFT necesario para HUGO
                    */
                        sh '''#!/bin/bash
                        
                        ls workspace | while read line; do

                            echo "line $line"
                        
                            #extract information from name
                            header="$(basename -- "$line" .md)"
                            name="${header#*__}"
                            version="${header%__*}"
                            version1="${version%%.*}"
                            version2="${version#*.}"
                            version2="${version2%.*}"
                            version3="${version##*.}"
                            
                            if [ ! -d "MDs/en/docs/$name" ]; then
                                mkdir -p MDs/en/docs/$name
                            fi
                            
                            if [ ! -d "DRAFT/en/docs/$name" ]; then
                            
                                mkdir -p DRAFT/en/docs/$name
                                
                                #create the _index.md file (required by hugo) for the endpoint
                                title=$(cat workspace/$line | grep -m 1 -h "title: " | head -1)
                                cd "DRAFT/en/docs/${name}"
                                
                                echo """---
"$title"
description: ""
draft: false
weight: 1
collapsible: true
---""" > _index.md
                                cd ../../../..
                            fi
                            
                            if [ ! -d "PUBLISH/en/docs/$name" ]; then
                                mkdir -p PUBLISH/en/docs/$name
                            fi
                            
                        done
                    '''
                    }
                }
            }
        }

        stage('Create Version Folders and Copy the File in MDs and Draft') {
            steps {
                script {
                    if( myAPIChanges.isAPIChanged()) {
                        /*
                    * Descripcion:
                    *   Si y solo si hay APIs afectadas:
                    * ---------Script bash
                    *  1. Para cada fichero en workspace
                    *  1.1 Se extrae la cabecera y el versionado del fichero,a si como el nombre del mismo
                    *  1.2 Se crea en MDs, PUBLISH, y DRAFT la carpeta dentro de en/docs/ con el nombre de la API sobre la que se esta iterando
                    *  1.3 Se crea _index.md en DRAFT necesario para HUGO
                    */
                        sh '''#!/bin/bash
                        
                        #create version folders
                        ls workspace | while read line; do
                        
                            #extract information from name
                            header="$(basename -- "$line" .md)"
                            name="${header#*__}"
                            version="${header%__*}"
                            version1="${version%%.*}"
                            version2="${version#*.}"
                            version2="${version2%.*}"
                            version3="${version##*.}"
                            
                            #create folder of the version in MDs
                            if [ ! -d "MDs/en/docs/${name}/${version1}" ]; then
                                
                                echo "created MDs/en/docs/${name}"
                                cd "MDs/en/docs/${name}"
                                mkdir ${version1}
                                cd ../../../..
                            fi
                            
                            #create folder of the version in DRAFT
                            if [ ! -d "DRAFT/en/docs/${name}/${version1}" ]; then
                                
                                echo "created DRAFT/en/docs/${name}"
                                #create folder of the version in DRAFT
                                cd "DRAFT/en/docs/${name}"
                                mkdir ${version1}
                                
                                #create the _index.md (required by hugo) file for the version
                                cd ${version1}
                                
                                echo """---
title: "V${version1}"
description: ""
draft: false
weight: $(( 100 - version2))
collapsible: true
---""" > _index.md
                                cd ../../../../..
                            fi
    
                            #copy file to MDs
                            cp workspace/$line MDs/en/docs/${name}/${version1}/${line}
                            
                            #copy file to draft
                            cp workspace/$line DRAFT/en/docs/${name}/${version1}/${line}
                            
                        done
                    '''
                    }
                }
            }
        }


        stage('Enrich Draft') {
            steps {
                script {
                    if( myAPIChanges.isAPIChanged()) {
                    /*
                    * Descripcion:
                    *   Si y solo si hay APIs afectadas:
                    * ---------Script bash
                    *  1. Para cada fichero en workspace
                    *  1.1 Se extrae la cabecera y el versionado del fichero,a si como el nombre del mismo
                    *  1.2 Se obtiene el enriquecido si aplica
                    *  1.3 Se realiza el enriquecido mediante git-merge con el fichero actual
                    * 
                    */
                        try {
                        sh '''#!/bin/bash
                            
                            ls workspace | while read line; do
                            
                                #extract information from name
                                header="$(basename -- "$line" .md)"
                                name="${header#*__}"
                                version="${header%__*}"
                                version1="${version%%.*}"
                                version2="${version#*.}"
                                version2="${version2%.*}"
                                version3="${version##*.}"
                                
                                
                            #enrich draft version based in previous Publish version
                                
                                if [ -n "$(ls -A "PUBLISH/en/docs/${name}/${version1}/" 2>/dev/null)" ]; then
                                
                                    #get Higher mid version value
                                    maxVersion2Infolder=$( ls --hide='_index.md' PUBLISH/en/docs/${name}/${version1}/ | sort -nr -t . -k 2 | head -n1)
                                    maxVersion2Infolder="$(basename -- "$maxVersion2Infolder" .md)"
                                    maxVersion2Infolder="${maxVersion2Infolder%__*}"
                                    maxVersion2Infolder="${maxVersion2Infolder#*.}"
                                    maxVersion2Infolder="${maxVersion2Infolder%.*}"
                                    
                                    #get Higher version file in folder
                                    highestVersionInFolder=$(ls PUBLISH/en/docs/${name}/${version1}/${version1}.${maxVersion2Infolder}.*  | sort -nr -t . -k 3  | head -n1)
                                    highestVersionInFolderName="$(basename -- "$highestVersionInFolder")"
                                    
                                    echo "highestVersionInFolder $highestVersionInFolder"
                                    
                                    #merge file with enriched file
                                    git merge-file \
                                        DRAFT/en/docs/${name}/${version1}/${line} \
                                        MDs/en/docs/${name}/${version1}/${highestVersionInFolderName} \
                                        PUBLISH/en/docs/${name}/${version1}/${highestVersionInFolderName}
                                    
                                fi
                            done
                        '''
                        }catch (err){
                            echo 'Enrichment of the DRAFT has failed'
                        }
                    }
                }
            }
        }
        
        stage('Clear') {
            steps {
                script {
                    /*
                    * Descripcion:
                    *   Si y solo si hay APIs afectadas:
                    * ---------Script bash
                    *  1. Se borran los fichero missing_commits_file, missing_changes_file
                    *   2. Se borra el directorio workspace
                    */
                if(myAPIChanges.isAPIChanged()) {
                    sh '''#!/bin/bash
                        if [[ -f missing_commits_file ]]; then
                            rm missing_commits_file
                        fi
                        if [[ -f missing_changes_file ]]; then
                            rm missing_changes_file
                        fi
                        rm -rf files workspace
                    '''
                    }
                }
            }
        }
        
        stage('Push to Git') {
            steps {
                script {
                    if( myAPIChanges.isAPIChanged()) {
                                            /*
                    * Descripcion:
                    *   Si y solo si hay APIs afectadas:
                    * ---------Script bash
                    *  0- Con las credenciales correspondientes
                    *  1. Se establece la url del repositorio remoto
                    *   2. Se establece el usuario y su email
                    * 3. Se realiza un commit con las APIs afectadas.
                    */
                        withCredentials([usernamePassword(credentialsId: '806bdc4e-af90-4255-83fc-b434c30a6720', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                            
                            sh '''#!/bin/bash
                                git remote set-url origin "https://${USERNAME}:${PASSWORD}@$UPLOAD"
                                git config user.email "HUGO AUTOMATED SYSTEM"
                                git config user.name  "HUGO AUTOMATED SYSTEM"
                                
                rm -rf DRAFT/en/docs/REAL_API_doc_swagger MDs/en/docs/REAL_API_doc_swagger

                                #push to documentation branch
                                git add -A
                                git commit -m "HUGO AUTOMATIC COMMIT"
                                git push --set-upstream origin HEAD:documentation
                                echo "Last affected commit:"
                                cat current_commit
                                '''
                        }
                    }
                }
            }
        }
    }
}