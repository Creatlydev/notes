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


</div>