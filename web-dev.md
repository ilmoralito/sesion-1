# Temas

- ¿Qué es el encabezado HTML?
- Encabezados y párrafos
- Creando hipervínculos
- Estructura del documento y del sitio web

# ¿Qué es el encabezado HTML?

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My test page</title>
  </head>
  <body>
    <p>This is my page</p>
  </body>
</html>
```
El contenido del encabezado `<head>...</head>` no se muestra en la página. En cambio, el trabajo del jefe es contener metadatos sobre el documento.

## Establecer el idioma principal del documento

Esto se hace agregando el atributo `lang` a la etiqueta HTML de apertura

```
<html lang="en-US">
```

Esto es útil de muchas formas. Su documento HTML será indexado de manera más efectiva por los motores de búsqueda si su idioma está configurado (lo que permite que aparezca correctamente en los resultados específicos del idioma, por ejemplo), y es útil para personas con discapacidades visuales que utilizan lectores de pantalla.

## Agregar un título

El elemento `<title>...</title>` es un metadato que representa el título del documento HTML general.

## Elementos `<meta>`

Los metadatos son datos que describen datos, y HTML tiene una forma "oficial" de agregar metadatos a un documento: el elemento `<meta>`.

Ejemplos:

- Especificar la codificación de caracteres de su documento `<meta charset="utf-8">`
- Agregar un autor y una descripción `<meta name="author" content="Ada Wong"> y <meta name="description" content="Lorem ipsum...">`

## Otros tipos de metadatos

Muchas de las funciones en los sitios web son creaciones patentadas, diseñadas para proporcionar a ciertos sitios (como los sitios de redes sociales) información específica que pueden usar. Por ejemplo, Open Graph Data es un protocolo de metadatos que Facebook inventó para proporcionar metadatos más completos para sitios web.

Ejemplo

```
<meta property="og:image" content="https://developer.cdn.mozilla.net/static/img/opengraph-logo.dc4e08e2f6af.png">
<meta property="og:description" content="The Mozilla Developer Network (MDN) provides
information about Open Web technologies including HTML, CSS, and APIs for both Web sites
and HTML5 Apps. It also documents Mozilla products, like Firefox OS.">
<meta property="og:title" content="Mozilla Developer Network">
```

Twitter también tiene sus propios metadatos patentados similares llamados Twitter Cards, que tienen un efecto similar cuando la URL del sitio se muestra en twitter.com.

```
<meta name="twitter:title" content="Mozilla Developer Network">
```

## Agregar iconos personalizados a un sitio

Es posible agregar referencias a iconos personalizados en metadatos, que se mostrarán en determinados contextos. El más utilizado es el favicon (abreviatura de "icono de favoritos", que se refiere a su uso en las listas de "favoritos" o "marcadores" de los navegadores).

El humilde favicon ha existido durante muchos años. Es el primer icono de este tipo: un icono cuadrado de 16 píxeles que se utiliza en varios lugares. Es posible que vea (según el navegador) favicons que se muestran en la pestaña del navegador que contiene cada página abierta y junto a las páginas marcadas en el panel de marcadores.

```
<link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
```

Hay muchos otros tipos de íconos a considerar en estos días. Por ejemplo

```
<!-- third-generation iPad with high-resolution Retina display: -->
<link rel="apple-touch-icon-precomposed" sizes="144x144" href="https://developer.cdn.mozilla.net/static/img/favicon144.a6e4162070f4.png">
<!-- iPhone with high-resolution Retina display: -->
<link rel="apple-touch-icon-precomposed" sizes="114x114" href="https://developer.cdn.mozilla.net/static/img/favicon114.0e9fabd44f85.png">
<!-- first- and second-generation iPad: -->
<link rel="apple-touch-icon-precomposed" sizes="72x72" href="https://developer.cdn.mozilla.net/static/img/favicon72.8ff9d87c82a0.png">
<!-- non-Retina iPhone, iPod Touch, and Android 2.1+ devices: -->
<link rel="apple-touch-icon-precomposed" href="https://developer.cdn.mozilla.net/static/img/favicon57.a2490b9a2d76.png">
<!-- basic favicon -->
<link rel="shortcut icon" href="https://developer.cdn.mozilla.net/static/img/favicon32.e02854fdcf73.png">
```

Los comentarios explican para qué se usa cada ícono: estos elementos cubren cosas como proporcionar un ícono agradable de alta resolución para usar cuando el sitio web se guarda en la pantalla de inicio de un iPad.

## Aplicar CSS y JavaScript a HTML

Se aplican más comúnmente a una página web utilizando el elemento `<link>` y el elemento `<script>`, respectivamente.

### CSS

El elemento `<link>` siempre debe ir dentro del encabezado de su documento. Esto toma dos atributos, `rel = "stylesheet"`, que indica que es la hoja de estilo del documento, y `href`, que contiene la ruta al archivo de la hoja de estilo

```
<link rel="stylesheet" href="my-css-file.css">
```

### JS

El elemento `<script>` también debe ir en el encabezado y debe incluir un atributo src que contenga la ruta al JavaScript que desea cargar y aplazar, que básicamente indica al navegador que cargue el JavaScript al mismo tiempo que el HTML de la página. Esto es útil ya que asegura que todo el HTML esté cargado antes de que se ejecute JavaScript, de modo que no obtenga errores como resultado de que JavaScript intente acceder a un elemento HTML que aún no existe en la página.

```
<script src="my-js-file.js" defer></script>
```

# Encabezados y párrafos

El contenido estructurado hace que la experiencia de lectura sea más fácil y agradable.

En `HTML`, cada párrafo debe estar envuelto en un elemento `<p>`, así:

```
<p>Lorem ipsum</p>
```

Cada encabezado debe estar envuelto en un elemento de encabezado:

```
<h1>Soy el título de la historia.</h1>
```

Hay seis elementos de encabezado: `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>` y `<h6>`. Cada elemento representa un nivel diferente de contenido en el documento; `<h1>` representa el encabezado principal, `<h2>` representa los subtítulos, `<h3>` representa los subtítulos secundarios y así sucesivamente.

Por ejemplo, en algun articulo, el elemento `<h1>` representa el título de la articulo, los elementos `<h2>` representan el título de cada seccion y los elementos `<h3>` representan subsecciones de cada seccion.

Algunas buenas prácticas a medida que crea dichas estructuras son:

- Preferiblemente, debe usar un solo `<h1>` por página; este es el encabezado de nivel superior y todos los demás se ubican debajo de este en la jerarquía.
- Asegúrese de utilizar los títulos en el orden correcto en la jerarquía.
- De los seis niveles de encabezado disponibles, debe intentar utilizar no más de tres por página, a menos que lo considere necesario.

## Semantica

Necesitamos asegurarnos de que estamos usando los elementos correctos, dando a nuestro contenido el significado, función o apariencia correctos.

## Lista

Hay tres tipos diferentes

- Desordenada
- Ordenada
- Listas de anidación

### Desordenada

Las listas desordenadas se utilizan para marcar listas de elementos para los que el orden de los elementos no importa.

```
<ul>
  <li>milk</li>
  <li>eggs</li>
  <li>bread</li>
  <li>hummus</li>
</ul>
```

### Ordenada

Las listas ordenadas son listas en las que el orden de los elementos sí importa.

```
<ol>
  <li>Drive to the end of the road</li>
  <li>Turn right</li>
  <li>Go straight across the first two roundabouts</li>
  <li>Turn left at the third roundabout</li>
  <li>The school is on your right, 300 meters up the road</li>
</ol>
```

### Listas de anidación

Está perfectamente bien anidar una lista dentro de otra. Es posible que desee tener algunas sub-viñetas debajo de una viñeta de nivel superior.

```
<ol>
  <li>Remove the skin from the garlic, and chop coarsely.</li>
  <li>Remove all the seeds and stalk from the pepper, and chop coarsely.</li>
  <li>Add all the ingredients into a food processor.</li>
  <li>Process all the ingredients into a paste.
    <ul>
      <li>If you want a coarse "chunky" hummus, process it for a short time.</li>
      <li>If you want a smooth hummus, process it for a longer time.</li>
    </ul>
  </li>
</ol>
```

## Énfasis, importancia, cursiva, negrita, subrayado ...

HTML proporciona varios elementos semánticos que permiten marcar contenido textual con efectos, veremos algunos de los más comunes.

### Énfasis

En HTML usamos el elemento `<em>` (énfasis) para marcar tales instancias. Además de hacer que la lectura del documento sea más interesante, los lectores de pantalla los reconocen y se pronuncian en un tono de voz diferente.

```
<p>I am <em>glad</em> you weren't <em>late</em>.</p>
```

### Importancia fuerte

En HTML usamos el elemento `<strong>` (gran importancia) para marcar tales instancias. Además de hacer que el documento sea más útil, nuevamente estos son reconocidos por los lectores de pantalla y hablados en un tono de voz diferente.

```
<p>This liquid is <strong>highly toxic</strong>.</p>
```

### Cursiva, negrita y subrayado

- `<i>` se utiliza para transmitir un significado tradicionalmente transmitido en cursiva: palabras extranjeras, designación taxonómica, términos técnicos, un pensamiento ...
- `<b>` se utiliza para transmitir un significado tradicionalmente en negrita: palabras clave, nombres de productos, oración principal ...
- `<u>` se utiliza para transmitir un significado tradicionalmente transmitido por el subrayado: nombre propio, falta de ortografía ... 

# Creando hipervínculos

Los hipervínculos son realmente importantes son los que hacen de la Web una Web.

Los hipervínculos son una de las innovaciones más interesantes que ofrece la Web. Han sido una característica de la Web desde el principio y son los que hace de la Web una red. Los hipervínculos nos permiten vincular documentos a otros documentos o recursos, vincular a partes específicas de documentos o hacer que las aplicaciones estén disponibles en una dirección web. Casi cualquier contenido web se puede convertir en un enlace de modo que cuando se hace clic o se activa de otra manera, el navegador web va a otra dirección web (URL).

Una URL puede apuntar a archivos HTML, archivos de texto, imágenes, documentos de texto, archivos de video y audio, o cualquier otra cosa que viva en la Web. Si el navegador web no sabe cómo mostrar o manejar el archivo, le preguntará si desea abrir el archivo (en cuyo caso el deber de abrir o manejar el archivo se transfiere a una aplicación nativa adecuada en el dispositivo) o descargue el archivo (en cuyo caso puede intentar tratar con él más adelante).

## Anatomía de un enlace

```
<a href="https://www.mozilla.org/en-US/">the Mozilla homepage</a>.
```

```
<a href="https://www.mozilla.org/en-US/" title="The best place to find more information about Mozilla's mission">the Mozilla homepage</a>.
```

## Enlaces a nivel de bloque

Casi cualquier contenido se puede convertir en un enlace

```
<a href="https://www.mozilla.org/en-US/">
  <img src="mozilla-image.png" alt="mozilla logo that links to the mozilla homepage">
</a>
```

### Fragmentos de documentos

Es posible vincular a una parte específica de un documento HTML, conocida como fragmento de documento, en lugar de solo a la parte superior del documento. Para hacer esto, primero debe asignar un atributo de identificación al elemento al que desea vincular

```
<h2 id="Mailing_address">Mailing address</h2>
```

Luego, para vincular a esa identificación específica, la incluiría al final de la URL, precedida por un símbolo #, por ejemplo:

```
<a href="contacts.html#Mailing_address">mailing address</a>
```

### Usar el atributo `download` al vincular a una descarga

Cuando se vincula a un recurso que se va a descargar en lugar de abrir en el navegador, puede utilizar el atributo `download` para proporcionar un nombre de archivo de guardado predeterminado.

```
<a
  href="https://download.mozilla.org/?product=firefox-latest-ssl&os=win64&lang=en-US"
  download="firefox-latest-64bit-installer.exe"
>
  Download Latest Firefox for Windows (64-bit) (English, US)
</a>
```

### E-mail links

Es posible crear vínculos o botones que, cuando se hace clic, abren un nuevo mensaje de correo electrónico saliente en lugar de vincular a un recurso o página. Esto se hace usando el elemento `<a>` y el esquema `mailto: URL`.

En su forma más básica y de uso común, un enlace `mailto`: indica la dirección de correo electrónico del destinatario previsto. Por ejemplo:

```
<a href="mailto:nowhere@mozilla.org">Send email to nowhere</a>
```
# Estructura del documento y del sitio web

HTML también cuenta con una serie de elementos de nivel de bloque que se utilizan para definir áreas de su sitio web tales como el encabezado, el menú de navegación, la columna de contenido principal, etc. Las páginas web pueden verse y se verán bastante diferentes entre sí, pero todas tienden a compartir componentes estándar similares

- Encabezamiento
- Barra de navegación
- Contenido principal
- Barra lateral
- Pie de página

Para implementar dicho marcado semántico, HTML proporciona etiquetas dedicadas que puede utilizar para representar dichas secciones.


- `<header>`
- `<nav>`
- `<main>` con varias subsecciones de contenido representadas por `<article>`, `<section>`, y elementos `<div>`
- `<aside>` a menudo colocado dentro `<main>`
- `<footer>`


# Multimedia

- Imagenes
  - Texto alternativo
  - Títulos de imágenes
  - Anotar imágenes con figuras y leyendas de figuras
  - Imágenes de fondo CSS
- Contenido de video y audio
  - El elemento `<video>`
  - Soporte de archivos de media en el navegador

## Imagenes

Para poner una imagen simple en una página web, usamos el elemento `<img>`.

Ejemplos

```
<img src="lala.jpg">
```

O bien

```
<img src="images/lala.jpg">
```

Es posible incrustar la imagen utilizando su URL absoluta.

```
<img src="https://www.example.com/images/lala.jpg">
```

> Pero esto no tiene sentido, ya que solo hace que el navegador trabaje más, buscando la dirección IP del servidor DNS de nuevo, etc. Casi siempre es mejor mantener las imágenes del sitio web en el mismo servidor que su HTML.

### Texto alternativo

El atributo `alt`. Se supone su valor es una descripción textual de la imagen, para usar en situaciones en las que la imagen no se puede ver, mostrar o tarda mucho en renderizarse debido a una conexión lenta a Internet.

```
<img src="images/lala.jpg" alt="Some text goes here">
```

### Títulos de imágenes

Al igual que con los enlaces, también puede agregarse el atributo `title` a las imágenes para proporcionar más información de apoyo si es necesario.

```
<img src="images/lala.jpg" alt="lorem ipsum" title="Some information goes here">
```

### Anotar imágenes con figuras y leyendas de figuras

Los elementos `<figure>` y `<figcaption>` proporcionan un contenedor semántico para las figuras, y vincular claramente la figura al título

```
<figure>
  <img src="images/lala.jpg" alt="Some text goes here">
  <figcaption>Lorem ipsum dolar sit ament</figcaption>
</figure>
```

### Imágenes de fondo CSS

```
p {
  background-image: url("images/dinosaur.jpg");
}
```

## Contenido de video y audio

Los desarrolladores web han querido usar video y audio en la Web durante mucho tiempo, desde principios de la década de 2000, cuando comenzamos a tener un ancho de banda lo suficientemente rápido para admitir cualquier tipo de video . En los primeros días, las tecnologías web nativas como HTML no tenían la capacidad de incrustar video y audio en la web, por lo que las tecnologías propietarias o basadas en complementos como Flash, y más tarde, Silverlight ambas ahora obsoletas. Se hizo popular por manejar dicho contenido. Este tipo de tecnología funcionaba bien, pero tenía una serie de problemas, como no funcionar bien con las funciones HTML/CSS, problemas de seguridad y problemas de accesibilidad.

Una solución nativa resolvería gran parte de esto si se implementara correctamente. Afortunadamente, unos años más tarde, la especificación HTML5 tenía tales características agregadas, con los elementos `<video>` y `<audio>`, y algunas nuevas y brillantes API de JavaScript para controlarlos. No veremos JavaScript aquí, solo los fundamentos básicos que se pueden lograr con HTML.

### El elemento `<video>`

El elemento `<video>` le permite incrustar un video muy fácilmente.

```
<video src="rabbit320.webm" controls>
  <p>Your browser doesn't support HTML5 video. Here is a <a href="rabbit320.webm">link to the video</a> instead.</p>
</video>
```

Ejemplo

https://mdn.github.io/learning-area/html/multimedia-and-embedding/video-and-audio-content/simple-video.html

### Soporte de archivos de media en el navegador

```
<video controls>
  <source src="rabbit320.mp4" type="video/mp4">
  <source src="rabbit320.webm" type="video/webm">
  <p>Your browser doesn't support HTML5 video. Here is a <a href="rabbit320.mp4">link to the video</a> instead.</p>
</video>
```

Otro ejemplo

```
<video controls width="400" height="400" autoplay loop muted preload="auto" poster="poster.png">
  <source src="rabbit320.mp4" type="video/mp4">
  <source src="rabbit320.webm" type="video/webm">
  <p>Your browser doesn't support HTML video. Here is a <a href="rabbit320.mp4">link to the video</a> instead.</p>
</video>
```

### El elemento `<audio>`

El elemento `<audio>` funciona casi igual que el elemento `<video>`

# Tablas HTML

Una tarea muy común en HTML es estructurar datos tabulares, y tiene una serie de elementos y atributos solo para este propósito.

Entre estas etiquetas se encuentran:

- `<table>`
  - `<thead>`
  - `<tbody>`
  - `<tfoot>`
  - `<tr>`
  - `<td>`
  - `<colgroup>`
  - `<caption>`

Una tabla es un conjunto estructurado de datos formado por filas y columnas (datos tabulares). Una tabla le permite buscar rápida y fácilmente valores que indican algún tipo de conexión entre diferentes tipos de datos.

Las tablas HTML deben usarse para datos tabulares; para esto están diseñadas. Desafortunadamente, mucha gente solía usar tablas HTML para diseñar páginas web, p. Ej. una fila para contener el encabezado, una fila para contener las columnas de contenido, una fila para contener el pie de página, etc.

## Añadiendo estructura con `<thead>`, `<tfoot>` y `<tbody>

Las etqieutas `<thead>`, `<tfoot>` y `<tbody>`, permiten marcar un encabezado, pie de página y sección del cuerpo de la tabla.

Estos elementos no hacen que la tabla sea más accesible para los usuarios de lectores de pantalla y no resultan en ninguna mejora visual por sí mismos. Sin embargo, son muy útiles para diseñar y diseñar, actuando como ganchos útiles para agregar CSS a su tabla.

## Tablas anidadas

Es posible anidar una tabla dentro de otra, siempre que incluya la estructura completa, incluido el elemento `<table>`. Por lo general, esto no es realmente recomendable, ya que hace que el marcado sea más confuso y menos accesible para los usuarios de lectores de pantalla, y en muchos casos también puede insertar celdas / filas / columnas adicionales en la tabla existente. Sin embargo, a veces es necesario.

```
<table id="table1">
  <tr>
    <th>title1</th>
    <th>title2</th>
    <th>title3</th>
  </tr>
  <tr>
    <td id="nested">
      <table id="table2">
        <tr>
          <td>cell1</td>
          <td>cell2</td>
          <td>cell3</td>
        </tr>
      </table>
    </td>
    <td>cell2</td>
    <td>cell3</td>
  </tr>
  <tr>
    <td>cell4</td>
    <td>cell5</td>
    <td>cell6</td>
  </tr>
</table>
```

# Formularios

El elemento HTML `<form>` representa una sección de documento que contiene controles interactivos para enviar información.

```
<form action="" method="get">
  <div>
    <label for="name">Enter your name: </label>
    <input type="text" name="name" id="name" required>
  </div>
  <div>
    <label for="email">Enter your email: </label>
    <input type="email" name="email" id="email" required>
  </div>
  <div>
    <input type="submit" value="Subscribe!">
  </div>
</form>
```

Mayor informacion https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form
