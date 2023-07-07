<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" integrity="sha512-iecdLmaskl7CVkqkXNQ/ZH/XLlvWZOJyj7Yy7tcenmpD1ypASozpmT/E0iPtmFIB46ZmdtAc9eNBvH0H/ZpiBw==" crossorigin="anonymous" referrerpolicy="no-referrer" />

<div align="center" style="font-size: 2rem;font-family: inconsolata;color: limegreen;font-weight: 900;">
    <i class="fa-solid fa-terminal"></i>  COMANDOS DE <i class="fa-brands fa-git-alt" style="color: #e09e10;"></i> GIT
</div>
<hr style="background-color: #222222;">

<!-- GIT INIT -->
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


<h2 style="color: #e09e10;font-weight: 800;">Archivo .gitignore</h2>
El archivo .gitignore se utiliza en Git para especificar qué archivos y directorios deben ser ignorados y no incluidos en el seguimiento del repositorio. Sirve para evitar que archivos innecesarios o sensibles sean incluidos accidentalmente en el repositorio, lo que puede causar ruido, aumentar el tamaño del repositorio y comprometer la privacidad.

<h3>Algunas nomenclaturas</h3>

```bash
# Ignorar todos los archivos con la extensión .txt
*.txt

# Ignorar un directorio llamado "docs" en la raíz del repositorio
/docs

# Ignorar un archivo específico llamado "important.txt"
important.txt

# Negar la exclusión de un archivo llamado "allowed.txt"
!allowed.txt
```

<h2 style="color: #e09e10;font-weight: 800;">git add</h2>
Este comando se utiliza para agregar las modificaciones realizadas al index (staging area) de git, lo que significa que los cambios quedan preparados para su confirmacion (commit)

<h3>Algunos usos de git add</h3>

```bash
# Agregar un archivo especifico al staging area
$ git add index.html
$ git add style.css

# Agregar al staging area todos los archivos modificados
$ git add .
```

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

</div>