---
title: Los labels y la usabilidad
date: "2013-11-20"
tags: [usabilidad]
---

Una de las cosas más engorrosas de maquetar (por lo menos para mí) son los formularios. No porque sea complejo, ni mucho menos, sino porque es una parte muy importante de la web que se suele dejar de lado.
<!--more-->

<br>
Quizás un formulario bien hecho puede incrementar la opinión del usuario sobre nuestra web, pero lo que es seguro es que un formulario mal hecho causa odio (o por lo menos rabia) hacia nuestra web.

<br>
Una de las tareas que solemos (y deberiamos) hacer para incrementar la usabilidad de los formularios de nuestra web, es añadir `labels` a los textos que nos identifican los campos a clicar. De esta manera, al clicar sobre el texto el foco se nos va al campo asociado, otorgándonos una gran facilidad para rellenar el campo.

<br>
Pero con este sisitema a veces puede surgir un problema: Si hay una separación entre el texto y el input, al clicar sobre ésta no pasará nada. Quizás pensemos que nadie "es tan tonto" como para clicar en lo blanco, pero no es así, seguramente nosotros lo hemos hecho muchas veces sin darnos cuenta (sobretodo si entramos desde dispositivos móviles, donde se requiere más precisión para clicar sobre el campo).

<br>
Así que para evitar esto, lo mejor que se puede hacer, tal y como me enseñó [Iván](https://twitter.com/ivan_gallego) (este tío es un crack), es anidar el input dentro del `label`, tal y como se muestra a continuación:

```html
<label for="name">
    <span>Nombre:</span>
    <input type="text" name="name" id="name" placeholder="Ej. Rafael">
</label>
```
De esta forma conseguimos que todo el area que los engloba sea clicable y nos lleve el foco al campo que deseamos.

<small class="right">Además podríamos darle un padding al `input` y así aumentar el area de click</small>
