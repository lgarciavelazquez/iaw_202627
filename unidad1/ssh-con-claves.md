# Trabajando con claves ssh

En el trabajo cotidiano de los administradores de sistemas una de las tarea que se hace a menudo es la **conexión remota a servidores** usando el protocolo **ssh**. Además de la posibilidad de usar nombre de usuario y contraseña para autentificarnos en la máquina remota, en este post vamos a estudiar otra manera de autentificación que nos proporciona ssh: Autentificación usando claves ssh también conocido como **Autenticación mediante clave pública/privada**. Les recuerdo que el SSH se explicará con mas detalle en otros módulo del curso.

Como casi siempre, escribo este artículo para mis alumnos, en esta ocasión, para mis alumnos de 2º del ciclo de grado superior  de Administración de Sistemas Informáticos y en Red. Vamos a ello:

## Entorno de trabajo

Vamos a trabajar con dos máquinas (o nodos) una cliente y otra servidor con el sistema operativo Linux Debian 13. 
<u>Nota</u>: Una de las máquinas puede ser tu host anfitrión realizando todos las acciones que se indican a continuación desde el terminal de *Git Bash*. 

Vamos a suponer dos nodos:

* **nodo1**: Actuará de cliente, desde donde nos vamos a conectar. Tiene la dirección IP `10.0.0.10` y hemos creado un usuario que hemos llamado **usuario**.
* **nodo2**: Actuará como servidor ssh, es la máquina a la que nos vamos a conectar. Tiene la dirección IP `10.0.0.11` y hemos creado un usuario que hemos llamado **usuario**.

Por lo tanto nos vamos a conectar desde la máquina `nodo1` con el usuario `usuario` a la máquina `nodo2` con el `usuario`.

## Creación de las claves ssh en el cliente

En la máquina cliente `nodo1`, el `usuario` va a crear sus claves ssh, en concreto, un par de claves pública/privada cifradas con el algoritmo RSA. Para generar las claves vamos a usar el comando `ssh-keygen` y durante la generación se nos solicita alguna información:

* **La ubicación y el nombre de las claves**: En principio el directorio donde se guarda es `.ssh` en el home del usuario, y el nombre puede ser cualquiera, pero para empezar os sugiero que dejéis el que viene por defecto `id_rsa`, de esta manera no habrá que indicar el nombre de la clave al realizar la conexión (se toma el nombre `id_rsa` por defecto). Por lo tanto en la primera pregunta dejamos los valores por defecto.
* **Frase de paso (passphrase)**: Se nos pide a continuación una palabra de paso. Por seguridad, os sugiero que la pongáis porque será la contraseña de vuestra clave privada. Al utilizar la clave privada se os pedirá la frase de paso. Si vuestra clave privada cae en malas manos necesitarán esta frase para poder usarla.

 <u>Nota</u>: En nuestro caso, para facilitar el trabajo vamos a dejar la clave de paso en blanco. 

<!--more-->

```
usuario1@nodo1:~$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/usuario/.ssh/id_rsa): 
Created directory '/home/usuario/.ssh'.
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/usuario/.ssh/id_rsa
Your public key has been saved in /home/usuario/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:FfyzzFqODXZi+sFeLei+1ILURDTmzHwt8khSUvj+TjY usuario@nodo1
The key's randomart image is:
+---[RSA 3072]----+
|        .=O      |
|        .X.o .   |
|        ..X.o .  |
|         *.=o.   |
|        S.oo.o   |
|       . o*o*.   |
|        .+*@E .  |
|        .+o*+o   |
|         o*o.    |
+----[SHA256]-----+
```

Si hacemos ahora un listado de los ficheros del directorio `~/.ssh`, aparecerán los ficheros:

```
usuario@cliente:~$ ls -l ~/.ssh/

usuario@nodo1:~$ ls -al .ssh
total 16
drwx------ 2 usuario usuario 4096 Jan 24 16:04 .
drwxr-xr-x 3 usuario usuario 4096 Jan 24 16:02 ..
-rw------- 1 usuario usuario 2655 Jan 24 16:04 id_rsa
-rw-r--r-- 1 usuario usuario  568 Jan 24 16:04 id_rsa.pub
...
```

* `id_rsa` es la clave privada del usuario adecuadamente protegida (permisos 0600). No la pierdas, esta clave te identifica. ¡Guárdala bien!.
 * `id_rsa.pub` es la clave pública del usuario.

## Configuración del servidor

Para que con nuestra clave privada podamos autentificarnos al conectarnos con ssh con el servidor, tenemos que copiar nuestra clave pública en el servidor. Copiaremos el contenido de la clave pública en el fichero `~/.ssh/authorized_keys` del usuario del servidor con el que vamos a realizar la conexión.

Para realizar esta copia vamos a usar la instrucción `ssh-copy-id` desde el cliente, indicando la clave pública que vamos a copiar:

```
usuario@nodo1:~$ ssh-copy-id -i .ssh/id_rsa.pub usuario@10.0.0.11
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: ".ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
usuario@10.0.0.11's password: 

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'usuario@10.0.0.11'"
and check to make sure that only the key(s) you wanted were added.
```

Ahora podemos comprobar en el servidor que en el home del `usuario` se ha creado un fichero `.ssh/authorized_keys` con el contenido de la clave pública del `usuario` del cliente:

```
usuario@nodo2:~$ ls -al .ssh
total 12
drwx------ 2 usuario usuario 4096 Jan 24 16:26 .
drwxr-xr-x 3 usuario usuario 4096 Jan 24 16:26 ..
-rw------- 1 usuario usuario  568 Jan 24 16:26 authorized_keys

usuario@nodo2:~$ cat .ssh/authorized_keys 
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC9WwLHgn7oJxGOyc7zCfEg+FFF/mL0pSkGsLHHb6wC+hvV4BDGBTfNrXEnDQvlLt+FmZ9Fv4fvFgfILbg2+ZEyMIuDDz1zcK8kJp5hcUQPksfAdVJGDLAdoj77qkKeb6uEZ6765aXYHh9sEY6A1hqsXitS9S007AvdYpZdd6Q4/5gwGNUlUw28fqDEoY1IjsC177yxvKXzgoL49Fl4ozf5bb6u9skugVpmzlfS3/ZRELtgCNgyxRnG3lP5Iu7NP8h9o58Eba/EHOtCUKV08UyfvDTFgPqoKiR0HntKAvqMTBsf/ZFbp99XSAkP+qli3KSBhQKIyMeqoha+n75NVY1/DTeW1uirfEVuUaQ/rBDBexib4kzj66c16AqqPIaFzV8z+UB5nZSA13I0XnkJkn/7pWcN9+4/gazH7kdGtqA0DSx7gOxw4ZrVMARK8i5QWKSeAJbfFdgHe4LEZiQ7KU/jYWltbXxNa+Xga5kpy1/UGlPvcE7k1KfGeqpqOvpju+0= usuario@nodo1
```

**Nota:** Podríamos copiar el contenido de la clave pública del cliente al servidor de forma manual, sin utilizar el comando `ssh-copy-id`. Simplemente tendríamos que copiar en el portapapeles el contenido del fichero `id_rsa.pub` en el cliente y pegarlo en el fichero `.ssh/authorized_keys` del servidor.

## Accediendo por ssh sin contraseña

Ahora desde el cliente podremos acceder desde el `usuario` (utilizando su clave privada) al `usuario` del servidor sin necesidad de introducir la contraseña de ese usuario, sin embargo como estamos usando la clave privada se nos pedirá la frase de paso:

```
usuario@nodo1:~$ ssh usuario@10.0.0.11
Enter passphrase for key '/home/usuario/.ssh/id_rsa': 
Linux nodo2 5.10.0-20-amd64 #1 SMP Debian 5.10.158-2 (2022-12-13) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Tue Jan 24 16:26:04 2023 from 10.0.0.10
usuario@nodo2:~$ 
```
