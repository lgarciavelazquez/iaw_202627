# Ejercicio 1: Introducción a git y GitHub

## ¿Qué vas a aprender en este ejercicio?

* Recordar el uso de git para realizar el control de versiones de los proyectos.
* Configurar una cuenta en GitHub, servicio que nos ofrece repositorios remotos.
* Recordar el ciclo de vida de la gestión de nuestros repositorios: creación, clonación, sincronización, ... y nuestros ficheros:  creación, modificación, borrado.

## ¿Qué tienes que hacer?

1. Crea una cuenta en GitHub (**Si no la tienes!!!**). La forma de acceder a los repositorios remotos de GitHub va a ser por SSH, por lo tanto debes copiar tu clave pública RSA a GitHub, para ello:

   * Genera una nueva clave ssh pública en el directorio `~/.ssh`, si no la tienes,   sigue las instrucciones del siguiente artículo: [Trabajando con claves SSH](ssh-con-claves.md)
   * Copia el contenido de tu fichero en tu perfil de GitHub `~/.ssh/id_rsa.pub`. Para ello, añade una nueva clave SSH en el apartado "SSH keys" de tu perfil en GitHub y pega el contenido de tu clave pública.
   * Para más información, lee el siguiente artículo: <https://docs.github.com/es/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account>
	 

**Nota IMPORTANTE**: Existen dos maneras diferentes de conectarse a GitHub de manera remota: conexión con `SSH` o `HTTPS` con autenticación con clave de paso o **token** . Si tienes problemas con SSH, puedes utilizar el `HTTPS`. 
En este caso debemos crear en primer lugar un **token** (tipo *classic*), una forma de autenticación necesaria para subir en remoto a nuestro repositorio. Para mas información, lee el siguiente artículo: <https://docs.github.com/es/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens>

Una vez creado el *token*, la conexión al repositorio remoto se puede hacer de dos maneras, donde `USERNAME` es el usuario de GitHub y `TOKEN` es el token:
```
* git remote add origin https://USERNAME:TOKEN@github.com/USERNAME/REPO.git  
* git clone https://USERNAME:TOKEN@github.com/USERNAME/REPO.git
```

1. Crea en GitHub un repositorio REMOTO con el nombre **prueba_tu_nombre** (**inicializa el repositorio** con un fichero README) y la descripción **Repositorio de prueba 2ASIR**.

2. Conéctate remotamente a una máquina virtual Linux Debian 12 e instala git  (**si no lo tienes instalado!!!**). **Nota**: Recuerda que desde Windows utiliza *Git Bash*.
```
		apt update
		apt install git
```

3. Configuración de git en la máquina virtual Linux. Lo primero que deberías hacer cuando instalas Git es establecer tu nombre de usuario y dirección de correo electrónico (**Asegurate que los datos son correctos y que has puesto tu nombre completo**). Esto es importante porque las confirmaciones de cambios (commits) en Git usan esta información, y es introducida de manera inmutable en los commits que envías, por ejemplo:
```
		git config --global user.name "John Doe"
		git config --global user.email johndoe@example.com
```
	De nuevo, sólo necesitas hacer esto una vez si especificas la opción `--global`, ya que Git siempre usará esta información para todo lo que hagas en ese sistema.

4. Clona el repositorio remoto en tu máquina virtual Linux Debian 12. Copia la url SSH del repositorio (**copia la url HTTPS si tienes problemas con URL SSH**) y vamos a clonar el repositorio en nuestro ordenador.

		git clone git@github.com:USERNAME/REPO.git

	Para comprobar que tienes configurado el repositorio usando la url SSH puedes ver el fichero de configuración en **.git/config**.

	Otra opción es utilizando el comando: `git remote -v`

	Comprueba que dentro del repositorio que hemos creado se encuentra el fichero README.md, en este fichero podemos poner la descripción del proyecto. Edita el fichero README.md y por el siguiente texto: **## Repositorio de prueba 2ASIR**

5. Vamos a crear dos ficheros, los vamos a añadir a nuestro repositorio local y luego lo vamos a sincronizar con nuestro repositorio remoto de GitHub. Cada vez que hagamos una modificación en el repositorio lo podemos señalar creando un commit. Los mensajes de los commits son fundamentales para explicar la evolución de un proyecto. Un commit debe ser un conjunto pequeño de cambios de los ficheros del proyecto con una cierta coherencia.
```
		echo "Este es el primer fichero" > ejemplo1.txt
		echo "Este es el segundo fichero" > ejemplo2.txt
		git add .
		git commit -m "He creado los ficheros ejemplo1 y ejemplo2"
		git push origin main
```
**Nota**: Asegúrate que la rama principal se llama *main*, `git branch -v`, si no es así debes cambiar el nombre de la rama principal: `git branch -M main` .

6. Cambia el texto de ejemplo1.txt por el siguiente: *Este es el primer archivo*. Si modificas un fichero en tu repositorio local, no es necesario volver a añadirlo a tu repositorio (`git add`). Pero tienes que usar la opción -a al hacer el commit. 
```
		git commit -am "He modificado el texto del fichero ejemplo1.txt"
		git push origin main
```
7. Si quieres cambiar el nombre de un fichero o directorio de tu repositorio:
```
		mv ejemplo1.txt example1.txt
		git commit -am "He cambiado el nombre del fichero ejemplo1 a example1"
		git push origin main
```
8.  Si quieres borrar un fichero de tu repositorio:
```
		rm ejemplo2.txt
		git commit -am "He borrado el fichero ejemplo2"
		git push origin main
```
9. Clona el repositorio en tu equipo Windows. Recuerda que puedes clonar tu repositorio de GitHub en varios ordenadores (por ejemplo, si quieres trabajar en tu casa). Comprueba que se ha clonado en tu equipo Windows.
 
10. Modifica con el editor de texto *nano* en el máquina virtual Linux Debian 12 el fichero **example1.txt** con el texto siguiente: 
```
This is the first file
Modified from Linux Debian.
```
Confirma el cambio y súbelo al repositorio remoto.  

11.  Comprueba que se ha actualizado el repositorio remoto.   
  
12.  Comprueba que el repositorio local en windows está con la versión antigüa del archivo *example1.txt*. Actualiza en el repositorio Windows los cambios que se hayan producido en el repositorio remoto, para ello ejecuta:   `git pull`

13.  Comprueba que se ha actualizado el repositorio local en Windows: `git status`

14.  Vamos a crear un nuevo repositorio llamado **prueba2_tu_nombre**. Ten en cuenta lo siguiente:
* En esta ocasión, crea primero el repositorio local en Windows (usando `git init`). El repositorio debe contener, al menos, dos archivos de texto: *archivo1.txt* y *archivo2.txt*. El contenido de ambos archivos es libre.
* Agrega (conecta) el repositorio local con un repositorio remoto en GitHub (usando `git remote add`).
* Sube el repositorio local a GitHub (usando `git push`).
* Clona el repositorio remoto en tu máquina virtual Linux Debian (usando `git clone`). 
* Modifica, en Windows, uno de los archivos y añade un 3º archivo de texto llamado *archivo3.txt*. Confirma los cambios(usando `git add`, `git commit`) y súbelos al repositorio (usando `git push`).
* Actualiza la versión local del repositorio en Linux Debian (usando `git pull`).
 

## ¿Qué tienes que realizar?

1. Crea un fichero en Markdown llamado `ejercicio1.md` donde documentes todos los pasos a realizar en el apartado 14. 
2. Sube el fichero `ejercicio1.md` al repositorio remoto que has creado en el ejercicio: **prueba_tu_nombre**.

