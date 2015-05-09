id: 2
title: Cómo organizar nuestros ficheros en Sass
~~~~~
Mucha gente que empieza con Sass no sabe cómo organizar su código, o que existe el método `@import` para poder importar otros ficheros (y que se compilen todo en uno).<br><br>

Una buena estructura y organización nos pueden hacer ser mucho más productivos y veloces a la hora de hacer cualquier modificación.<br><br>

Aviso que voy a explicar estándares que se han ido implementando, pero también lo voy a mezclar con otros que yo he ido adquiriendo con la prática y que me han ayudado a ser más productivo.
<!--more-->
### Estructurando nuestro código
Lo primero antes de empezar cada proyecto es preparar nuestro directorio básico de ficheros<br><br>

Antes de ponerme a explicar cómo está formado prefiero poner el ejemplo de directorios que tiene éste blog y luego comentarlo.

<?prettify?>

    sass/
    |- libs/
    |   |- bourbon/
    |   |   |- // Archivos de bourbon...
    |   |- neat/
    |   |   |- // Archivos de neat...
    |   |- _base.scss
    |   |- _fonts.scss
    |   |- _keyframes.scss
    |   |- _normalize.scss
    |   |- _reset.scss
    |- blog.scss

Si te fijas, verás como todos los archivos menos el `blog.scss` empiezan por una barra baja ('_'). Esto es un estándar que se ha adquirido en Sass. Todo archivo que va a ser incluído en otro ha de ser precedido por una barra baja. Pero no te preocupes al hacer las importaciones, allí n ohace falta añadir la barra baja, Sass te la añadirá automaticamente al compilar!<br><br>

Por ahora vamos a ignorar las carpetas [bourbon]() y [neat](), que son dos librerías que explicaré en otro post.<br><br>

El archivo `blog.scss` es el encargado de incluir el fichero `_base.scss` y éste, es el responsable de incluir a los demás.<br><br>

Actualmente, el fichero `_base.scss` luce así:

<?prettify?>

    @import "bourbon/bourbon";
    @import "neat/neat";

    @import "normalize";
    @import "reset";

    @import "fonts";
    @import "keyframes";

Como se puede ver, éste sólo contiene imports, nada más. Aquí llegamos a un *punto de conflicto*, hay gente que opina que las variables generales se han de situar aquí, otros que en un fichero aparte y algunos, cómo yo, que se han de poner en el fichero principal antes de importar el `base.scss`.<br><br>

Opino así ya que son variables, que sobretodo en los primeros momentos de desarrollo de un sitio, van a ser modificadas bastantes veces y no hay sitio más cómodo para ir modificándolas que en el fichero principal.<br><br>

Así, por ejemplo, podemos ver que el fichero `blog.scss` empieza de esta forma:

<?prettify?>

    /* Variables generales
    --------------------------------------------- */
    $max-width: em(1300);
    $gutter: golden-ratio(.7em, 1);

    /* Importación de librerias
    --------------------------------------------- */
    @import "libs/base";

    /* Variables locales
    --------------------------------------------- */
    // Colores
    $color-background: #f5f5f5;
    $color-base:       #10D177;
    $color-secondary:  #FAF4B1;
    $color-great:      #E1D772;
    $color-important:  #45AAB8;
    $color-text:       #484848;

    // Fuentes
    ...

<small class="right">Sí, lo sé, tengo una forma muy chula de comentar, quizás lo escriba en otro post :P</small><br><br>

Teniendo una estructura similar podremos escalar muy bien nuestros proyectos además de que mantenerlos será mucho más fácil, tanto si es para nosotros solos cómo si es para nuestro equipo.<br><br>

Cualquier duda, no dudes en comentar!

<small class="right">Post dedicado a [@sergiGP](http://sergigp.com)</small>
