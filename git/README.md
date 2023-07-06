<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" integrity="sha512-iecdLmaskl7CVkqkXNQ/ZH/XLlvWZOJyj7Yy7tcenmpD1ypASozpmT/E0iPtmFIB46ZmdtAc9eNBvH0H/ZpiBw==" crossorigin="anonymous" referrerpolicy="no-referrer" />

<div align="center" style="font-size: 2rem;font-family: inconsolata;color: limegreen;font-weight: 700;">
    <i class="fa-solid fa-terminal"></i>  COMANDOS DE <i class="fa-brands fa-git-alt" style="color: #e09e10;"></i> GIT
</div>
<hr style="background-color: #222222;">

<!-- GIT INIT -->
<div style="font-family: inconsolata;"> 

<h2 style="color: #e09e10;">git init</h2>
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

<h2 style="color: #e09e10;">git config</h2>
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



</div>