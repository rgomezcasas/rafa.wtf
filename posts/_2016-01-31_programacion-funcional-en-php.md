id: 5
title: Programación funcional en php
~~~~~
A medida que vamos "mejorando" como programadores también vamos añadiendo, sin querer, más complejidad a nuestro código. Esta complejidad (comúnmente llamada sobreingeniería) hace que nuestro código sea más "difícil" de entender para otros, y por lo tanto, hace que el desarrollo se vuelva algo más lento y tedioso.

No hay ninguna fórmula mágica para evitar esta complejidad, nomás nos queda la experienca y el poder aprender de nuestros errores y del de los demás. 

La programación functional nos puede ayudar a reducir parte de esta complejidad a través de abstraer funcionalidad en la composición de pequeñas funciones.

Un pequeño ejemplo de algo complejo en php podría ser lo siguiente:

```
<?php

$tags = 'comment, php, important, swag';
$tags = explode(', ', $tags);

foreach ($tags as $key => $value) {
    if (strlen($value) <= 4) {
        unset($tags[$key]);
    }
}

return $tags;

```
Quizás lo veas y pienses que no es complejo, y que si no se entiende lo extraes a un método con un buen nombre y ya se entenderá. Pero nada del otro mundo, el día que otra persona haya de entrar allí por x motivo seguramente se acabe acordando de tu madre.

En ese ejemplo, casi sin darnos cuenta, nos hemos puesto a jugar con el estado. Al principio `$tags` era un string, luego ha pasado a ser una lista y luego ha acabado siendo una lista más corta. Jugar con el estado suele conllevar (en el 90% de los casos) complejidad adicional.

Otra misma forma de hacer lo mismo podría ser:


```
<?php

$tags = 'comment, php, important, swag';

$tagsBiggerThan4CharsFilter = function ($tag) {
    return strlen($tag) > 4;
};

return array_filter(explode(', ', $tags), $tagsBiggerThan4CharsFilter);

```

Quizás esta forma te resulte un poco más "rara" al principio, al fin y al cabo es acostumbrarse a leerlo, pero siendo lo mismo, esta es una manera mucho más fácil de leerlo que la previa ya que es mucho más fácil leer "estoy filtrando todo los tags que contienen más de 3 letras" a decir "por cada tag que tengo dentro de mi lista si éste contiene 4 o menos caracteres me lo quitas de la misma".
