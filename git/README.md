<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" integrity="sha512-iecdLmaskl7CVkqkXNQ/ZH/XLlvWZOJyj7Yy7tcenmpD1ypASozpmT/E0iPtmFIB46ZmdtAc9eNBvH0H/ZpiBw==" crossorigin="anonymous" referrerpolicy="no-referrer" />

<div align="center" style="font-size: 2rem;font-family: inconsolata;color: limegreen;font-weight: 900;">
    <i class="fa-solid fa-terminal"></i>  COMANDOS DE <i class="fa-brands fa-git-alt" style="color: #e09e10;"></i> GIT
</div>
<hr style="background-color: #222222;">

<!-- &GIT INIT -->
<div style="font-family: inconsolata;"> 

<h2 style="color: #e09e10;font-weight: 800;">git init</h2>
Este es el primer comando que se ejecuta para empezar a trabajar con git, 
lo que hace es inicializar un nuevo repositorio git

<h3>Usos</h3>

```bash
# Crear un repositorio vacio en el directorio actual
$ git init
# Crea un repositorio vacion en el subdirectorio especificado
# si el directorio no existe crea uno nuevo
$ git init <directory>
$ git init appNote
```

<!-- &GIT CONFIG -->
<h2 style="color: #e09e10;font-weight: 800;">git config</h2>
Este comando se utiliza para definir valores de configuracion de git a nivel de un proyecto global o local

<h3>Usos</h3>

```bash
# Establece un nombre al repositorio actual, esta configuracion
# solo se aplicara a dicho respositorio
$ git config user.name "Tu Nombre"

# Establece un email al repositorio actual, esta 
# configuracion solo se aplicara a dicho repositorio
$ git init user.email "Tu email"

# Establecer nombre a nivel global
$ git config --global user.name "Tu nombre"
$ git config --global user.name "Samir"

# Establecer email a nivel global
$ git config --global user.email "Tu email"
$ git config --global user.email "samir@gmail.com"

# Las configuraciones son importantes para que git sepa quien
# realizo los commits en el historial de cambios del repositorio
# Ademas cada que desees puedes sobreescribir estos valores para cierto respositorio

# Puedes ver la lista de configuracion actual a nivel global de git
$ git config --global --list

# O bien ver las configuraciones del repositorio actual
$ git config --list

# Estos comandos mostraran las configuraciones actuales, incluyendo tu nombre
# de usuario y email

# Configurar que editor deberia de utilizar git
# UTILIZAR NANO
$ git config --global core.editor "nano -w"

# UTILIZAR VIM
$ git config --global core.editor "vim"

# git config se puede usar para configurar alias de manera global o local
$ git config --global alias.<nombre-alias> <"comando que se ejecutara">
$ git config alias.myalias "push origin main"

# Resultados coloreados
# color.ui es una variable maestra para los colores de git
# Se utiliza para activar o desactivar los resultados coloreados en git
$ git config --global color.ui [false | always | auto]
```

<!-- &ALIAS DE GIT -->
<h2 style="color: #e09e10;font-weight: 800;">Alias de GIT</h2>
Alias es sinonimo de "acceso rapido" . Los alias se usan para crear nombres cortos
para comandos mas largos, no existe un comando 'git alias' como tal, sino que
se mediante el comando git config y los archivos de configuracion, como sucede con los demas valores de configuracion los alias se pueden crear tanto a nivel local como global.


<h3>Ejemplos de como funcionan los alias de git</h3>

```bash
$ git config --global alias.co checkout
$ git config --global alias.br branch
$ git config --global alias.ci commit
$ git config --global alias.st status
```

<i>en los ejemplos de codigo anterior, se crean alias para los comandos mas habituales de git, ademas con el parametro '--global' estamos diciendo que estos alias estaran disponibles a nivel global en todo el sistema operativo , por lo que seran almacenados en el archivo de configuracion de git '.gitconfig'
Mayormente en windows este archivo se encuentra en el directorio principal del usuario
</i>

```bash
[alias]
        co = checkout
        br = branch
        ci = commit
        st = status
```

<h3>Uso de alias para crear nuevos comandos de GIT</h3>

```bash
# Alias para realizar un reset del area de preparación
$ git config --global alias.unstage "reset HEAD --"
# Ahora se puede realizar un reset del area de ensayo ejecutando.
$ git unstage
$ git unstage index.html
# Esto seria equivalente a ejecutar
$ git reset HEAD --
$ git reset HEAD -- index.html

# Crear alias que ejecuta una secuencia de comandos en lugar de un unico documento
# El siguiente alias, ejecuta dos comandos
# Primero se cambia a la rama main
# y luego se realiza un pull
$ git config --global alias.lgb "checkout main && git pull"
# Bastara con llamar al alias llamado 'lgb' para ejecutar los dos comandos
$ git lgb
# Equivalente a 
$ git checkout main
$ git pull

# Eliminar un alias de git, si se ha creado globalmente
$ git config --global --unset alias.<nombre-alias>
# Eliminar un alias de git, creado localmente
$ git config --unset alias.<nombre-alias>

```
<i>
En resumen los alias de git son una potente herramienta que optimiza el flujo de trabaja, ahorrando el numero de teclas pulsadas para ejecutar un comando, ya que permite crear nombres mucho mas cortos que a su vez ejecuta comandos muchos mas largos comandos repetitivos. Al usarlos te permitira programar de una forma mucho mas rapido y efeciente
</i>

<!-- &GIT CLONE -->

<h2 style="color: #e09e10;font-weight: 800;">git clone</h2>
el comando 'clone' sirve para realizar una copia de un repositorio existente, puede ser un repositorio local como remoto, basicamente 'git clone' apunta a un repositorio existente y copia toda su estructura e historial en un directorio de tu maquina

<h3>Ejemplos de git clone</h3>

```bash
# Realizar la clonacion de un repositorio remoto, por ejemplo alojado en Github
$ git clone <url-repository>

# Clonar repositorio a una carpeta especifica
$ git clone <url-repo> <directory>

# Clonacion de una etiqueta especifica
$ git clone --branch <tag> <repo>

# Clonacion superficial
$ git clone -depth=1 <repo>
# Lo que hace el comando anterior es clonar unicamente 
# el historial de confirmaciones (commits) especificado por el parametro -depth, 
# en dicho solo se esta clonando la confirmacion mas reciente del repositorio. 
# Esto es util para cuando el historial de confirmaciones
# del repositorio es bastante largo  y entre otras cosas
# te puedes ahorrar un largo tiempo de espera en la clonacion
```

<!-- &GITIGNORE -->

<h2 style="color: #e09e10;font-weight: 800;">Archivo .gitignore</h2>
El archivo .gitignore se utiliza en Git para especificar qué archivos y directorios deben ser ignorados y no incluidos en el seguimiento del repositorio. Sirve para evitar que archivos innecesarios o sensibles sean incluidos accidentalmente en el repositorio, lo que puede causar ruido, aumentar el tamaño del repositorio y comprometer la privacidad.

<h3>ejemplos de expresiones y convenciones</h3>

```bash
# Ignorar todos los archivos de un tipo en especifico
*.txt
*.log
*.test

# Ignorar tipos de archivos
# Utilizando los [] se puede especificar un grupo de tipos de archivos que deseas ignorar
*[.txt, .docx, .xlsx]

# Ignorar archivos en todos los directorios y subdirectorios con el mismo nombre
**/archivo.log

# Ignorar todos los archivos de un tipo en especifico en todos los subdirectorios
**/*.log

# Ignorar un directorio llamado "Docs" en la raíz del repositorio
/Docs se refiere a una carpeta "Docs" en el directorio raíz del repositorio.

# Ignorar un directorio llamado "Docs" en cualquier subdirectorio
Docs/ se refiere a cualquier carpeta "Docs" en cualquier nivel de subdirectorio en el repositorio.

# Ignorar un archivo específico llamado "important.txt"
important.txt

# Negar la exclusión de un archivo ene especifico "filename.txt"
!filename.txt

# Excluir subdirectorios en un directorio en especifico
carpeta-principal/*
!carpeta-principal/subcarpeta/
!carpeta-principal/subcarpeta/*

# Ignorar todos los archivos de un respositorio excepto un archivo en especifico
carpeta/*
!carpeta/archivo.txt


---------------------------------------------------------------------------------
# PATRONES DE COINCIDENCIA MULTIPLE
# -> Ignorar todos lor archivos que empiezen con config seguido de un numero
config[0-9]*
# Esto ignorará archivos como config1.txt, config2.txt, etc.

```

<!-- &GIT STATUS -->

<h2 style="color: #e09e10;font-weight: 800;">GIT status</h2>
Este comando permite visualizar el estado de los archivos existentes en el repositorio
Existen dos estados principales :

```markdown
-> Rastreados (Tracked File) : son todos los archivos que estaban en la ultima instantanea
    Pueden estar:
        -> Sin modificar
        -> Modificados   (M)
        -> Preparados    (A)
-> No Rastreados (Untracked) : Son todos aquellos archivos que no existian en la ultima instantanea
```

<h3>Algunos usos de git status</h3>

```bash
# Ver estado de archivos
$ git status

# Ver de forma simplificada el estado de cada uno de los archivos
$ git status -s
# o
$ git status --short

# ?? -> Archivos sin seguimiento (Untracked File)
# A  -> Archivos preparados para el proximo commit
# M  -> Arhivos modificados
```

<h2 style="color: #e09e10;font-weight: 800;">git add</h2>
Este comando se utiliza para agregar las modificaciones realizadas al index (staging area) de git, lo que significa que los cambios quedan preparados para su confirmacion (commit)

<!-- &GIT ADD -->

<h3>Algunos usos de git add</h3>

```bash
# Agregar un archivo especifico al staging area
$ git add index.html
$ git add style.css

# Agregar al staging area todos los archivos modificados
$ git add .

# Agregar archivos filtrados
# Por ejemplo agregar todos los archivos .txt
$ git add *.txt

# Agregar todos los archivos .txt y .py y .md
$ git add *.txt *.py *.md
```

<!-- &GIT COMMIT -->

<h2 style="color: #e09e10;font-weight: 800;">git commit</h2>
El comando 'commit' se utiliza para confirmar los cambios que previamente se han agregado al staging area (usando 'git add'), esto lo que hace es confirmar una nueva instantanea del estado del proyecto al historial de cambios de git

<h3>Algunos usos de git commit</h3>

```bash
# Confirmar nuevo cambio y agregar el mensaje del commit
$ git commit -m "mensaje descriptivo del cambio"

# O puedes solo ejecutar 'git commit', esto 
# abrira el editor que tienes asociado a git para
# escribir el mensaje del nuevo commit
$ git commit

# Supongamos que has hecho modificaciones en algunos archivos
# Y deseas commitearlos hacer un commit
# Pero deses una forma rapida sin tener que primero
# hacer 'git add' y luego 'git commit -m'
# Pues para esto existe la opcion '-am' de commit
$ git commit -am "mensaje descriptivo"
# el comando anterior lo que hace es ejecutar dos comandos, primero hace 'un git add'
# luego el commit directamente
# OJO: este comando funciona solo para archivos modificados, no para nuevos archivos
# es decir archivos que ya tienen un historial en git
```


<h2 style="color: #e09e10;font-weight: 800;">git diff</h2>
Este comando se utiliza para mostrar las diferencias entre estados de git, por ejemplo para comparar los cambios del estado actual del repositorio con el estado que tenia en cierto commit

<!-- &GIT DIFF -->

<h3>Algunos usos de git diff</h3>

```bash
# Mostrar las diferencias de los archivos entre el area de preparacion
# y el directorio de trabajo
$ git diff

# Diferencias entre commits
$ git diff <commit1> <commit2>

# Diferencias entre el directorio de trabajo (Working directory)
# Y un commit en especifico
$ git diff <commit>

# Diferencias entre el commit mas reciente (HEAD) y el directorio de trabajo (Working directory)
$ git diff HEAD

# Diferencias entre ramas, para mostrar cambios de una rama
# en comparacion a otra
$ git diff <rama1> <rama2>

# Mostrar diferencias entre index (Staging area) y el ultimo commit
# se puede hacer con la opcion '--cached | --staged'
$ git diff --staged
$ git diff --cached

# Opcion para mostrar solo los nombres de los archivos modificados
# sin mostrar los diferencias reales '--name-only'
$ git diff --name-only <resto_de_opciones>

# Mostrar el nombre y el estado de los archivos modificados
$ git diff --name-status <resto_de_opciones>

# Mostrar la diferencias de palabras en lugar de lineas completas
# Color verde para adiciones, y color rojo para eliminacion de palabras
git diff --color-words <resto_de_opciones>

# Mostrar un resumen estadistico de las diferencias
$ git diff --stat
```

<!-- &GIT LOG -->

<h2 style="color: #e09e10;font-weight: 800;">git log</h2>
Este comando se utiliza para visualizar el historial de commit que has realizado en el tiempo, ademas que te permite agregar opciones de formato para poder visualizar el historial de una forma mas grafica y concisa

<h3>Algunos usos de git log</h3>

```bash
# El mas simple es ejecutar 'git log' sin ninguna opcion adicional
# esto listara el historial de commit de tu repositorio git
$ git log

# '--oneline' mostrar la lista de commits en una sola linea
# Con el hash abreviado y el mensaje descriptivo del commit
$ git log --oneline

# '--graph' te permite ver el historial en forma de grafico ASCII, 
# Se puede visualizar de manera mas grafica las relaciones entre commits y ramas
git log --graph

# Opciones de filtracion del historial de commits
# Filtrar los commits por autor, para ello deberas especificar
# El nombre o correo electronico del autor
$ git log --author="Creatlydev"
$ git log --author="correo_de_autor"

# Filtrar por mensaje de commit especifico o patron de busqueda
git log --grep="bug fix"

# Filtrar commits por fecha o un rango de fechas
# A partir de una fecha hasta el commit actual
$ git log --since="2023-07-04"
# Tambien se puede incluir a partir de que hora
$ git log --since="2023-07-04 10:30:00"

# Rango de fechas, esto limitara los commits dentro del rango
git log --since="2023-07-02" --until="2023-07-6"

# Filtrar por fechas relativas
# '2 weeks ago' : Muestra commits realizados en las ultimas dos semanas
# '1 month ago' : Muestra commits del ultimo mes
# '3 months ago' : Muestra commits de los ultimos 3 meses
git log --since="1 month ago" --until="2 weeks ago"
# El comando anterior mostrara los commit en el ultimo mes, pero no en las ultimas dos semanas

# Visualizar los cambios introducidos en cada commit '--patch | -p'
$ git log --patch
$ git log -p

# Mostrar resumen estaditistico de cada commit
$ git log --stat

# '--decorate', muestra las referencias, como ramas y etiquetas, junto a los commits en la salida
git log --decorate

# Limitar el numero de commits que se desea mostrar '-n'
$ git log -n 5
# El comando anterior mostrara solo los ultimos cinco commits

# '--all' para mostrar todos los commits, de todas las ramas existentes
$ git log --all
```

<!-- &GIT CHECKOUT -->

<h2 style="color: #e09e10;font-weight: 800;">git checkout</h2>
Este comando sirve para ejecutar diferentes acciones, con el se puede revisar commits anteriores, cambiar de rama e incluso crear una nueva rama y el uso mas comun de descartar cambios de un arhivos o archivos

<h3>Algunos usos de git checkout</h3>

```bash
# Cambiar a una rama existente del repositorio para trabajar en ella
$ git checkout <name-branch>

# '-b' Esta opcion te permite crear una nueva rama y al mismo tiempo situarte en esa nueva rama
$ git checkout -b <name-new-branch>

# Revisar un commit especifico
$ git checkout <hash-commit>
# Cuando se ejecuta el comando anterior GIT se situa en un 
# estado llamado "modo de desprendimiento" (detached HEAD state)
# Lo que significa que ahora el no estas en una rama especifica
# el puntero HEAD que siempre señala el ultimo commit agregado
# Ahora apunta el commit especifico que has especificado en el comando
# Es un estado temporal donde no podras realizar cambios directamente,
# Este estado puede ser util para revisar versiones anteriores del respositorio
# O experimentar, pero es recomendable crear una nueva rama a partir de ese commit en especifico
# esto si se desea preservar los cambios y continuar trabajando en ellos, y posteriormente realizar una merge
# con la rama principal

# Para crear una nueva rama a partir de ese punto y siturate en ella al mismo tiempo
# se puede realizar con el siguiente comando
$ git checkout -b <name-new-branch> <hash-commit>

# Moverse a un commit <n> commits anteriores al HEAD
$ git checkout HEAD~<n>
$ git checkout HEAD~2
$ git checkout HEAD~5

# Cambiar rapidamente entre la rama actual y la rama anterior
# En la que estabas trabajando
$ git checkout -

# Descartar cambios de un archivo o varios archivos
$ git checkout -- <name-file>
# El (--) doble guion bajo indica que lo que sigue a partir de ahi
# son nombres de archivos y no opciones, todo lo escrito despues de los (--)
# GIT asume que se trata del nombre de un archivo

# Descartar todos los cambios realizados en los distintos archivos
$ git checkout -- .
# Al ejecutar el comando anterior se descartaran todos los cambios del repositorio
# incluso los archivos que no estan rastreados por git , osea en estado (Untracking)
```

<!-- &GIT RESET -->

<h2 style="color: #e09e10;font-weight: 800;">git reset</h2>
Este comando se utilizar para deshacer cambios, mover ramas y para actualizar la posicion del encabezado de rama HEAD

<h3>Algunos usos de git reset</h3>

```bash
# Mover la rama actual y posicion del encabezado de rama HEAD al commit especificado
$ git reset <hash-commit>

# Deshacer cambios agregados al area de preparacion (Unstage Changes)
$ git reset HEAD --

# Opciones adicionales a git reset
* --soft  : Reset suave, mantiene los cambios desechos de los commits en el area de preparacion
* --mixed : (Predeterminado) reset mixto, esta opcion elimina los cambios desechos de los commits del area de 
            preparacion pero mantiene las modificaciones en el directorio de trabajo (Working Directory)
* --hard  : Esta opcion deshace los commits y desecha los cambios tanto del area de preparacion
            como del directorio de trabajo, pierdes las modificaciones posteriores
            al commit que especificaste realizar el reset

$ git reset --soft <hash-commit>
$ git resest --mixed <hash-commit>
$ git reset  --hard  <hash-commit>

# Realizar un reset a un commit <n> commits anteriores al HEAD
$ git reset HEAD~<n>
$ git reset HEAD~3
$ git reset HEAD~1
```

<!-- &GIT TAG -->

<h2 style="color: #e09e10;font-weight: 800;">git tag</h2>
Este comando se utiliza para crear, listar y administrar etiquetas(Tags).
Las etiquetas son referencias a puntos especificos de la historia del repositorio (Apunta a un commit)
Generalmente son usadas para marcar versiones importantes o hitos en el proyecto

<h3>Algunos ejemplos del comando git tag</h3>

```bash
# Creacion de una etiqueta ligera
# Estas etiquetas son simplemente un puntero a un commit especifico sin metadatos adicionales
$ git tag <name-tag> <hash-commit>
$ git tag v1.0.0 abc123

# Creacion de etiqueta anotada
# Este tipo de etiqueta es un objeto commpleto en si mismo y contiene información 
# adicional como el autor, la fecha y el mensaje 
# opion '-a'
$ git tag -a <name-tag> <hash-commit>
$ git tag -a v1.0.0 abc123

# Etiqueta anotada con mensaje en linea
$ git tag -a <name-tag> <hash-commit> -m <description-tag>
$ git tag -a nombre-etiqueta -m "Este es el mensaje de la etiqueta"

# Listar todas las etiquetas
$ git tag

# Visualizar detalles de una etiqueta 
$ git show <name-tag>


# Eliminar una etiqueta en local
$ git tag -d <name-tag>
$ git tag --delete <name-tag>

# Enviar etiquetas locales al repsoitorio remoto
# El siguiente comando envia todas las etiquetas creadas al repositorio remoto
$ git push origin --tags

# El siguiente envia a una etiqueta en especifico
$ git tag origin <name-tag>

# Eliminar una etiqueta remota
$ git push --delete origin <nombre-etiqueta>
$ git push -d origin <nombre-etiqueta>
$ git push --delete origin version_beta
```

<!-- &GIT SHOW -->

<h2 style="color: #e09e10;font-weight: 800;">git show</h2>
Este comando se utiliza para mostrar información detallada de objetos en el repositorio comot, commits, tags, árboles y blobs, proporciona una vista ampliada y completa de un objeto

<h3>Algunos ejemplos de su uso</h3>

```bash
# Ver información de un commit
$ git show <hash-commit>

# Mostrar información de una etiqueta
$ git show <name-tag>
# opciones
* --stat -> Mostrara un resumen de los cambios en los archivos asociados a la etiqueta
* --summary -> Mostrar un resumen aun mas corto acerca de la etiqueta
* --name-only -> Muestra solo el nombre de los archivos modificados

# Mostrar cambios realizados en un commit
$ git show -p <hash-commit>
$ git show --patch <hash-commit>
```

<!-- &GIT BRANCH -->

<h2 style="color: #e09e10;font-weight: 800;">git branch</h2>

Este comando sirve para crear, enumerar, renombrar y eliminar sucursales (Ramas) , una rama en git es una linea de desarrollo independiente a tu rama principal del repositorio, esto te permite desarrollar una funcionalidad o corregir algun bug de forma aislada sin comprometer el codigo principal, cuando ya termines la nueva funcionalidad puedes fusionar todos los commits de esa rama con la rama principal, pero para esto no basta solo con el comando git branch, sino que se ayuda con los comandos de  `git checkout` o  `git switch` para cambiar entre las ramas que tengas creadas y el comando  `git merge` para fusionar los cambios

<h3>Algunos usos de git branch</h3>

```bash
# Listar las ramas locales
$ git branch  
$ git branch --list

# Listar las ramas remotas
$ git branch -a

# Crear nueva rama
$ git branch <new-branch>

# Renombrar rama 
$ git branch -m <new-name-branch

# Eliminar una rama (Seguro)
$ git branch -d <name-branch>
# El comando anterior es seguro ya que si tienes cambios que no has fusionado 
# git te advertira que si eliminas la rama perderas esa linea de desarrollo

# Eliminar rama (Forzado)
$ git branch -D <name-branch>
# Este comando elimina la rama sin importar 
# que haya cambios que nos hayas fusionado

# Subir rama local a repositorio remoto
$ git push <name-remote-repo> <branch-name>
$ git push origin Feature

# Eliminar rama del repositorio remoto
$ git push origin --delete <name-branch>
$ git push origin :<name-branch>
$ git push origin --delete Feature
$ git push origin :Feature

# ver el último commit de cada rama, puedes utilizar la opción -v.
$ git branch -v
```

<!-- &GIT MERGE -->

<h2 style="color: #e09e10;font-weight: 800;">git merge</h2>
se utiliza para combinar los cambios de una rama con otra rama activa (generalmente la rama actual). Esto permite integrar los cambios realizados en una rama en otra, lo que es útil para incorporar nuevas características, correcciones de errores o actualizaciones.

<h3>Algunas opciones de git merge</h3>

```bash
# Fusionar rama especifica con la rama actual
$ git merge <new-feature>
# Cuando se realiza un merge y no ocurre ningun conflicto, se crea un commit automatico
# Puedes desactivar este comportamiento con la opcion  --no-commit
# Fusionar sin commit automatico
$ git merge <name-rama> --no-commit

# Para cancelar | abortar un merge en curso utiliza la opcion --abort
$ git merge --abort
```

<!-- &GIT SWITCH -->

<h2 style="color: #e09e10;font-weight: 800;">git switch</h2>

El comando `git switch` es una alternativa más simple y segura al uso de los comandos `git checkout` y `git branch` en ciertas situaciones. El comando `git switch` se utiliza para cambiar entre ramas existentes o crear y cambiar a una nueva rama en un solo paso. Es especialmente útil para cambiar de rama sin preocuparse por crear conflictos o modificar accidentalmente archivos en la rama actual.

<h3>Algunas opciones del comando git switch</h3>

```bash
# Cambiar a una rama existente
$ git switch nombre-de-la-rama

# Crear y cambiar a una nueva rama
$ git switch -c nombre-de-la-rama
```

<!-- &GIT STASH -->

<h2 style="color: #e09e10;font-weight: 800;">git stash</h2>

El comando `git stash` almacena temporalmente (o guarda en un stash) los cambios que hayas efectuado en el código en el que estás trabajando para que puedas trabajar en otra cosa y, más tarde, regresar y volver a aplicar los cambios más tarde.

<h3>Algunas opciones del comando git stash</h3>

```bash
# Guardar cambios en un stash
# Esto guardara los cambios no comiteados en un estado 
# WIP (Work In ´Progress)
$ git stash

# Se puede contextualizar un poco agregando un mensaje
# al stash creado con <save>
$ git stash save 'Add style to our site'

# Ver listado de stashes
$ git stash list

# Volver a aplicar los cambios de stash
$ git stash pop
# Al hacer pop del stash, se eliminan los cambios de este y se 
# vuelven a aplicar en el código en el que estás trabajando.

# Otra opción es volver a aplicar los cambios en el código en el 
# que estás trabajando y conservarlos en tu stash mediante el 
# comando git stash apply:
$ git stash apply
# Esto resulta útil si quieres aplicar los mismos cambios de un 
# stash en varias ramas.

# Almacenar archivos en un stash que esten ignorados o sin 
# seguimiento

# Si añadimos la opción -u (o --include-untracked), se indica a 
# git stash que también guarde en el stash los archivos 
# sin seguimiento
$ git stash -u
$ git stash --include-untracked

# También puedes incluir los cambios en los archivos 
# ignorados utilizando la opción -a (o --all) al ejecutar 
# el comando git stash.
$ git stash -a
$ git stash --all

# De forma predeterminada, git stash pop volverá a aplicar 
# el último stash creado: stash@{0}. Puedes especificar el 
# stash que deseas aplicar poniendi su identificadir
# como ultimo argumento
$ git stash pop stash@{2}
# Lo mismo aplica para la opcion apply

# Ver un resumen de un stash
$ git stash show

# Otra opción es utilizar la opción -p (o --patch) para ver 
# todas las diferencias de un stash:
$ git stash show -p

# Si decides que ya no necesitas algún stash en particular, puedes eliminarlo mediante el comando:
$ git stash drop stash@{1}

# Si lo que deseas es eliminar todos los stashes utiliza:
$ git stash clear


```

</div>

