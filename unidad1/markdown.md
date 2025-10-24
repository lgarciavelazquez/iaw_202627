# TUTORIAL DE MARKDOWN

## Qué es Markdown

 Markdown es un lenguaje de marcado con el que puedes agregar formato a documentos de texto plano. Fue creado por John Gruber en el año 2004, siendo a día de hoy uno de los lenguajes de marcado más famosos. Su popularidad se debe a que es sencillo, ligero y fácil de aprender por parte de aquellas personas que no tienen un perfil técnico.

## Porqué usar Markdown

 * **Muy versátil**. Permite crear documentos, notas, libros, documentaciones, emails e incluso los textos de cualquier web.
 * **Formato muy establecido**. Se puede usar en gestores de contenidos (CMS), foros y aplicaciones sociales. Por ejemplo, Markdown es el formato que se utiliza por defecto  en GiHub y en casi en cualquier herramienta relacionada con el mundo de la programación.
 * **Independiente de la plataforma**. Podrás crear documentos Markdown en cualquier sistema operativo.
 * **Portable**. los archivos Markdown pueden ser abiertos con cualquier editor de texto. Si has creado un documento con un editor pero luego cambias de idea y prefieres usar otro, podrás abrir el documento en el nuevo editor sin realizar conversiones de ningún tipo.
 * **Perdura en el tiempo**. Aunque la aplicación que uses deje de estar soportada y ya no funcione. El hecho de saber que cualquier persona podrá abrir un documento Markdown dentro de 30 años es uno de los motivos por los que una gran cantidad de textos académicos se crean en formato Markdown.

## Cómo funciona Markdown

### Edición de documentos

Cuando redactas un documento en formato Markdown y lo guardas, se almacenará como un documento de texto plano que podrá contener la extensión **.md**, **.markdown** o incluso **.mdx** en caso de que quieras agregar funcionalidades adicionales.

Puedes crear un archivo Markdown con cualquier editor de texto plano. Bastará con que apliques la sintaxis Markdown deseada. Sin embargo, es recomendable que uses un editor compatible que resalte la sintaxis Markdown, más que nada por cuestiones de usabilidad, ya que te resultará más cómodo editar los documentos.

### Procesado de documentos

Para renderizar los documentos en formato Markdown en algún formato como HTML, primero deben ser procesados. Hemos dicho HTML, pero podríamos haber dicho cualquier otro formato como PDF.

Para procesar documentos Markdown necesitas usar alguna aplicación que sea capaz de hacerlo. La buena noticia es que a día de hoy existen montones de aplicaciones que son capaces de procesar texto en formato Markdown, ya sean simples scripts de conversión o editores como LibreOffice Writer o Microsoft Word. A estas aplicaciones se les suele denominar como procesadores o parsers de Markdown.

### Herramientas de apoyo

El mejor modo de aprender a usar Markdown quizás sea utilizarlo. Para ello puedes usar alguna de las múltiples herramientas gratuitas existentes como el Notepad++ o Visual Studio Code si lo prefieres.

## Para qué se utiliza Markdown

Markdown se utiliza para la creación de documentos, notas, documentaciones, libros o sitios web.

La sintaxis de Markdown permite crear documentos y tomar notas con rapidez, pudiendo crear desde pequeños artículos hasta libros enteros que luego podrás imprimir o exportar a PDF.

La sintaxis de Markdown es relativamente sencilla y, una vez aprendida, podrás editar cualquier documento desde cualquier lugar, creando nuevas entradas para tu blog, escribiendo emails, creando listas de elementos o redactando el siguiente capítulo para tu libro.

### Páginas web

Uno de las premisas principales que llevó a la creación de Markdown fue su uso en Internet, y por ello existen decenas de herramientas que te permitirán crear contenido para sitios web con la sintaxis Markdown.

Si sabes usar HTML o CSS, tienes a tu disposición generadores de sitios estáticos como Jekyll o Hugo que usarán los archivos Markdown y los estilos que apliques para crear una web estática que podrás publicar en cualquier servidor o servicio de hosting básico. Existen servicios como Netlify o GitHub Pages que te permitirán publicar webs estáticas gratuitamente.

Si usas WordPress, has de saber que ahora también dispone de soporte para Markdown desde la incorporación del editor de bloques. Si usas el editor antiguo, podrás agregar soporte para Markdown mediante Jetpack.

## Sintaxis básica de Markdown

En este taller de introducción a Markdown aprenderemos los comandos básicos para empezar a trabajar. 

1. [Encabezados](#encabezados)
2. [Bloques de texto](#bloques-de-texto)
3. [Formato de texto](#formato-de-texto)
4. [Código](#código)
5. [Listas](#listas)
6. [Vínculos o enlaces](#vínculos-o-enlaces)
7. [Imágenes](#imágenes)
8. [Tablas](#tablas)
9. [Ver código fuente markdown](https://github.com/lumigv/iaw_202324/raw/gh-pages/unidad1/markdown.md)


### Encabezados

Los encabezados se crean usando el carácter sostenido # delante de la oración que quieras que se formatee como un encabezado. Los encabezados pueden ser de diferentes niveles, organizándose jerárquicamente. Para crear encabezados de diferentes niveles debes agregar tantos símbolos # seguidos como el nivel del encabezado.

# H1 o primer nivel
## H2 o segundo nivel
### H3 o tercer nivel
#### H4 o cuarto nivel
##### H5 o quinto nivel
###### H6 o sexto nivel

### Bloques de texto

#### Párrafos

Para generar un nuevo párrafo basta simplemente separar el texto mediante una línea en blanco **pulsando 2 VECES INTRO**:

Esto es un párrafo.

Y esto es otro párrafo.

#### Saltos de línea

Para añadir un salto de línea y empezar en una línea siguiente dentro del mismo párrafo basta con dejar **dos o mas espacios en blanco** al final de la línea y luego pulsas **INTRO**.  

    
Esto es una línea.  
Y esta es otra línea.
 
#### Cita o Blockquote

Para agregar citas en Markdown debes agregar el signo mayor > justo delante de una línea o de un párrafo:

> Esta es la cita  1  
> Continuación de la cita 1
> > cita 3


### Formato de Texto

#### Negrita

**Texto en negrita**  
__Texto en negrita__

#### Itálica o cursiva

*Texto en itálica*  
_Texto en itálica_

#### Negrita cursiva

***Texto en negrita cursiva***  
___Texto en negrita cursiva___


### Código

#### Código en línea

Para agregar código en línea en Markdown tendrás que usar **comillas invertidas** alrededor del texto que quieres que tengo formato de código:

`codigo`


#### Bloque de código

Si el código que quieres agregar consta de más de una línea, puedes agregar un bloque de código. para ello basta con que uses al **menos cuatro espacios** o una **tabulación** al inicio de la línea:

    Creando códigos de bloque.  
    Puedes añadir tantas líneas como quieras.

También se puede generar con 3 **comillas invertidas**:

```
Creando códigos de bloque.  
Puedes añadir tantas líneas como quieras.
```

### Listas

En Markdown puedes agregar tanto listas ordenadas como no ordenadas. Las listas no ordenadas contienen enlaces que siguen un orden secuencial, mientras que las no ordenadas contienen elementos ordenados arbitrariamente.

#### Lista ordenada

Para agregar listas ordenadas en Markdown debes agregar un número seguido de un punto, un espacio y el elemento de la lista. La lista no debe estar ordenada numéricamente, pero debe comenzar por el número 1:

1. Primer elemento
2. Segundo elemento
3. Tercer elemento


#### Lista desordenada

Para agregar listas no ordenadas en Markdown debes agregar un guion -, un signo más + o un asterisco * delante de los elementos de la lista:

Ejemplo 1:

- Primer elemento
- Segundo elemento
- Tercer elemento

Ejemplo 2:

* Primer elemento
* Segundo elemento
* Tercer elemento

Ejemplo 3:

+ Primer elemento
+ Segundo elemento
+ Tercer elemento

#### Anidación de listas

Puedes anidar las listas de diferentes tipos, incluyendo listas dentro de otras listas, ya sean odenadas o no ordenadas. Para ello, los elementos de la lista anidada tendrán que tener una sangría de al menos cuatro espacios o una tabulación:

Ejemplo 1:

* Elemento 1
    - Elemento 1
    - Elemento 1
* Elemento 2
* Elemento 3

Ejemplo 2:

1. Elemento 1
   * uno
   * dos
   * tres
2. Elemento 2
3. Elemento 3

Ejemplo 3:

1. Elemento 1
   1. Elemento 1
   2. Elemento 1
2. Elemento 2
3. Elemento 3
  
Ejemplo 4:

- Elemento 1
- Elemento 2
    * Elemento 2.1
    * Elemento 2.2
      + Elemento 2.2.1
      + Elemento 2.2.2  

### Línea horizontal

Para crear una línea horizontal basta con que agregues tres o más asteriscos seguidos, tres o más guiones seguidos o tres o más guiones bajos seguidos:

---
***
___

### Vínculos o enlaces

Para crear un enlace debes situar **entre corchetes** el texto que quieres enlazar, también conocido como anchor. Seguidamente, debes usar **paréntesis** para definir la URL a la que debe enlazar en texto del enlace

#### Enlaces a Tutoriales de Markdown

[Tutorial Markdown](https://tutorialmarkdown.com/)  
[Markdown cheat sheet](https://www.markdownguide.org/cheat-sheet/)

#### Enlace de un artículo a otro

[articulo1](articulo1.md)  
[articulo2](../articulo2.md)  
[articulo3](directorio/articulo3.md)


#### Enlace de marcador

Use un símbolo de **almohadilla** seguido de las palabras del título en minúscula. El **id** de la sección a enlazar se forma quitando los signos de puntuación del título y reemplazando los espacios por guiones:

[Bloques de texto](#bloques-de-texto)  
[Párrafo1](../articulo1.md#parrafo1)


#### URL

Se puede **crear enlaces rápidamente** a una URL usando únicamente un enlace, sin necesidad de definir un texto de enlace o anchor. Para ello deberás escribir un símbolo **menor** seguido del enlace y un símbolo **mayor**:

<https://www.markdownguide.org>


#### Correo electrónico

<me@email.com>

### Imágenes

Para agregar imágenes con Markdown debes agregar un **signo de exclamación !** seguido del **texto alternativo** o **alt** de la imagen entre corchetes y de la **URL de la imagen** entre paréntesis

#### Imágenes desde un archivo

![Markdown](img/logomarkdown.png "logo Markdown")


Hay que tener mucho cuidado al subir la imagen a un servidor web, en este caso sería recomendable incluir la / al principio. Podría mostrarse en el ordenador, pero no al servidor web.


![Markdown](/img/logomarkdown.png "logo Markdown")


#### Imágenes desde un ENLACE DEFINITIVO

![Linux](https://www.markdownguide.org/assets/images/tux.png)


#### Añadir un título a la imagen

Es posible agregar un título a la imagen, que se correpsonderá con el atributo HTML **title**. Para ello, basta con que agregues el título del enlace **entre comillas** después del enlace, en el interior de los paréntesis:

![Markdown](img/logomarkdown.png "logo Markdown")


### Tablas

Para agregar tablas Markdown debes definir las cabeceras de columna mediante al menos **tres guiones ---** que se situarán por debajo del texto de la cabecera. Para separar las diferentes cabeceras tendrás que usar un **símbolo de tubería |**:

#### Crear tabla

| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Row 1    | Cell 2   | Cell 3   |
| Row 2    | Cell 5   | Cell 6   |
| Row 3    | Cell 8   | Cell 9   |


#### Alineación

Puedes alinear los elementos de una tabla en el centro, a la derecha o a la izquierda usando **dos puntos :** en uno de los lados que definen la cabecera de la tabla para alinear su contenido a la izquierda o a la derecha respectivamente. Para alinear el contenido de la tabla en el centro, debes usar un **símbolo : a cada lado de los guiones**.


| Left-Aligned  | Center Aligned  | Right Aligned |
|:------------- |:---------------:| -------------:|
| Row 1         | Cell 2          | Cell 3        |
| Row 2         | Cell 5          | Cell 6        |
| Row 3         | Cell 8          | Cell 9        |









