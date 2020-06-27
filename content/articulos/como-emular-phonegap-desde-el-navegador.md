---
title: Cómo emular phonegap desde el navegador
date: "2014-04-30"
tags: [phonegap]
---

Una de las cosas que más molesta al estar desarrollando en Phonegap (o Apache Cordova) es tener que ir compilando y ejecutando (en nuestro emulador de Android/iOs/... o directamente en nuestros terminales) cada vez que queremos ver los cambios realizados, ya que esto tarda tiempo y tiempo...

Muchos hemos ido utilizando un "truquillo" para ir viéndolo en tiempo real: Abrir el archivo `index.html`desde el navegador. Con esto podemos ir viendo los cambios que vamos realizando, pero no nos es suficiente, ya que nosotros queremos poder utilizar las `api's` del teléfono (queremos poder usar la geolocalización, el acelerómetro...)

Pero todo problema tiene una solución, y en este caso la nuestra se llama:

### Apache Ripple
[Apache Ripple](http://ripple.incubator.apache.org/) era una [famosa extensión para el Google Chrome](https://chrome.google.com/webstore/detail/ripple-emulator-beta/geelfhphabnejjhdalkjhgipohgpdnoc) reconvertida en un [paquete de node.js](https://www.npmjs.org/package/ripple-emulator). Este cambio lo hicieron para aumentar la interoperabilidad (así la gente que use Firefox, Safari o cualquier otro navegador podría utilizarlo igual).

Mucha gente sigue usando la extensión en lugar del paquete npm, si estás usando phonegap o cordova versión 2 no hay problema, pero si estás usando la versión 3 esta extensión ya no es compatible (al menos sin realizar "guarradas").

Ripple funciona en entornos Linux y Mac y su instalación es muy fácil. Suponiendo que ya tenemos node.js y npm instalado (que si estás usando Apache Cordova o Phonegap los has de tener sí o sí), ejecutamos el siguiente comando desde nuestra terminal: `npm install -g ripple-emulator` (quizás te haga falta precederlo de un `sudo`) y ya estará instalado.

Su uso también es muy sencillo, tan solo tenemos que ir a la ruta de nuestro proyecto de Apache Cordova o Phonegap y ejecutar: `ripple emulate --path platforms/android/assets/www` (ten en cuenta que vas a estar emulando la plataforma según la carpeta que elijas, en este caso, android).

Al ejecutar el comando se nos abrirá una ventana en el navegador con una url similar a: `http://localhost:4400/?enableripple=cordova-3.0.0` donde podremos ver ya nuestra aplicación emulada y un seguido de operaciones a poder realizar (enviar coordenadas falsas, emular un "shake"...)

Ten en cuenta que cuando estamos trabajando con Apache Cordova o Phonegap trabajamos sobre la ruta `<Directorio del Proyecto>/www` y que Ripple emula directamente sobre la carpeta de la plataforma específica, así que si queremos ver los cambios que hemos realizado debemos de ejecutar sobre el directorio de nuestro proyecto el comando `cordova prepare`(`phonegap prepare` si usamos Phonegap) y luego ir a la pestaña de nuestro navegador donde se está ejecutando el Ripple y refrescar.

Este último proceso quizás es un poco tedioso (pero aun así, es infinitamente más rápido que tener que ir yendo compilando y ejecutando todo cada vez).

En un próximo post explicaré cómo automatizar este último punto usando [gulp.js](http://gulpjs.com/), para que cada vez que hagamos una modificación en nuestro proyecto, éste se `auto-prepare`y se refresque automáticamente la pestaña del navegador.

<small class="right">Si alguien lo prueba en Windows y funciona, por favor, que lo comente :)</small>

