---
identifier: 1
layout: post
title: "Minificar el HTML generado por Laravel 4"
tags: laravel
redirect_from:
  - /blog/p/minificar-el-html-generado-por-laravel-4/
---

Es muy común querer que tu web cargue más velozmente (aunque sólo sean unas décimas) y aún lo es más, que el responsable de SEO de tu empresa te exija optimizaciones en la velocidad de carga. Una de ellas es minificar el HTML resultante.
En Laravel esto es muy fácil, tan sencillo como pegar este [gist](https://gist.github.com/DotZecker/6786469 "Gist para minificar el HTML en Laravel 4") en `` /app/filters.php ``.
<!--more-->

<br>
El gist contiene:

```php
<?php

App::after(function($request, $response) {
    if (App::Environment() == 'production') {
        if ($response instanceof Illuminate\Http\Response) {
            $output = $response->getOriginalContent();

            $filters = array(
                '/<!--([^\[|(<!)].*)/' => '', // Borra los comentarios HTML
                '/<(?<!\S)\/\/\s*[^\r\n]*/' => '', /* Borra los comentarios */
                '/<\s{2,}/' => '', // Combina los espacios
                '/<(\r?\n)/' => '', // Elimina los saltos de linea
            );

            $output = preg_replace(
                array_keys($filters), array_values($filters), $output
            );

            $response->setContent($output);
        }
    }
});
```

<small class="right">Mi gist es un fork de [éste](https://gist.github.com/garagesocial/6059962 "Gist para minificar el HTML en Laravel 4") de [garagesocial](https://gist.github.com/garagesocial).</small>
