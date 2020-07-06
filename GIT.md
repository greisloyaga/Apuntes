# **GIT DESDE CERO**

- **Configuración de Git**
  - `git config`
  - `git config --l  / git config-list`  : lista las configuraciones de git 
  - podemos editar el usuario y el email
- **Iniciando el repositorio**
  - ​	`git init` : iniciamos el repositorio

- **Estados de git:**

  1. **Espacio de trabajo (working directory)** :  Es todo lo que podemos ver en la carpeta , menos la carpeta .git
     - `git status` : muestra un estado de como esta mi repositorio
     - `git add` : Mover los archivos del *espacio de trabajo* al área de preparación, uno a la vez
     - `git add .`: Agregar todos los archivos de la carpeta actual donde estoy 

  2. **Área de preparación(stage area)**
     - `git checkout -nombre del archivo`  `git checkout -f` : Deshacer los últimos cambios
     - `git diff styles/global.css` : ver cambios realizados en cada archivo ,antes de hacer commit
     - `git restore --staged NOMBRE_ARCHIVO`: Quitar archivos del área de preparación
     - `git commit -m "MENSAJE"` : Pasar los archivos del área de preparación al repositorio 
     - `git commit -am "MENSAJE"`: En un solo paso todos los **archivos modificados** van a pasar al área de preparación ya al repositorio

  3. Repositorio (carpeta .git) (git directory - repository)**
     - *`git log` para ver todos los mensaje del commit*
     - Historial de cambios :
       - `git checkout` 60bcfef (es el hash del commit)  para ir a otra versión anterior y recuperar alguna función,etc
       - `git checkout master` volvemos al ultimo commit
     - Opciones de visualización del historial
       - `git log --online` : muestra el hash resumido y el mensaje del commit . Sirve para listar los commit
       - `git log --online --all` : muestra información de commits  de todas las ramas tanto de la master y las otras ramas
       - `git log --oneline --all --graph --decorate`
       - `git log --oneline -n NUMERO` :  Ejm git log --online -n 5 , te trae 5 commits

- **Creando ramas locales**
  - `git checkout -b NOMBRE_RAMA` : Ejm git checkout -b development
  - `git branch` : lista todas las ramas
  - `git checkout NOMBRE_RAMA` o `git switch NOMBRE_RAMA` : para cambiar de rama 

- **Fusionando ramas locales**
  - `git merge NOMBRE_RAMA` : Ejem git merge development
  - `git branch -D NOMBRE_RAMA`: eliminando ramas locales 
  - `git merge -abort`: abortar la unión de las ramas

- **Ignorando archivos**
  - `.gitignore`: permite ignorar archivos o carpetas
    - requisitos.txt
    - ./pages
    - ./styles
    - index.html

- **Manejando ramas remotas**
  - `git clone http.....` :  clonar un proyecto de GitHub

- **Subiendo nuestros cambios a Github**
  -  `git remote add origin https://github.com/Greis15/git-desde-cero.git`  : subir tu proyecto  a GitHub 
  - `git remote -v`  : push/ fetch
  - `git push origin` : subir los cambios y empujar código a la nube
    - `git push origin master` : subir todos los cambios de local a GitHub (remote)
  - `git fetch origin :` traer la información  desde la nube
  -  `git pull origin master` :  traer información remota , jalar la información de la nube a la pc (local)

- **Crear ramas remotas**
  - Subir rama 
    - `git push origin NOMBRE_RAMA` : Ejem git push origin test
  - Borrar rama
    - `git push --delete origin NOMBRE_RAMA`

