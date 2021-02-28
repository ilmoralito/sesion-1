# CSS (Cascading Style Sheets)

CSS (hojas de estilo en cascada) se utiliza para dar estilo y diseñar páginas web, por ejemplo, para modificar la fuente, el color, el tamaño y el espaciado de su contenido, dividirlo en varias columnas o agregar animaciones y otras características decorativas.

Temas

- ¿Qué es CSS?
  - Aplicar CSS a HTML
    - Hoja de estilo externa
    - Hoja de estilo interna
    - Estilos en línea
  - Sintaxis CSS
    - Selectores
    - Especificidad
- Empezando con CSS
  - Añadiendo CSS a un documento
  - Añadiendo la etiqueta `<style>` en el elemento `<head>` de un documento HTML
  - Añadiendo el atributo `style` en alguna etiqueta del documento HTML 
  - Aplicar estilo a elementos HTML
  - El atributo `class`
  - Aplicar estilo a las cosas según su ubicación en un documento
- Cómo está estructurado CSS
- Cómo funciona CSS
- El modelo de caja
  - ¿Qué es el modelo de caja CSS?
    - Partes de la caja
  - El modelo de caja CSS estándar
  - Utilice DevTools del navegador para ver el modelo de caja
  - Márgenes, relleno y bordes
    - Margen
    - Bordes
    - Relleno
  - Bloque en línea

## ¿Qué es CSS?

CSS (hojas de estilo en cascada) permite crear páginas web de gran apariencia.

CSS se puede utilizar para un estilo de texto de documentos muy básico, por ejemplo, cambiar el color y el tamaño de los encabezados y enlaces. Se puede utilizar para crear diseño, por ejemplo, convertir una sola columna de texto en un diseño con un área de contenido principal y una barra lateral para información relacionada. Incluso se puede utilizar para efectos como animación.

## Aplicar CSS a HTML

Existen tres métodos para aplicar CSS a un documento: con una hoja de estilo externa, con una hoja de estilo interna y con estilos en línea.

### Hoja de estilo externa

Una hoja de estilo externa contiene CSS en un archivo separado con extensión `.css`. Este es el método más común y útil para incorporar CSS a un documento. Puede vincular un solo archivo CSS a varias páginas web, diseñando todas con la misma hoja de estilo CSS.

Se hace referencia a una hoja de estilo CSS externa desde un elemento HTML `<link>`

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My CSS experiment</title>
    <link rel="stylesheet" href="styles.css">
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>This is my first CSS example</p>
  </body>
</html>
```

El archivo de hoja de estilo CSS podría ser así

```
h1 {
  color: blue;
  background-color: yellow;
  border: 1px solid black;
}

p {
  color: red;
}
```

El atributo href del elemento `<link>` debe hacer referencia a un archivo en el sistema de archivos. En el ejemplo anterior, el archivo CSS está en la misma carpeta que el documento HTML, pero puede colocarlo en otro lugar y ajustar la ruta. A continuación, se muestran tres ejemplos:

Dentro de un subdirectorio llamado estilos dentro del directorio actual

`<link rel="stylesheet" href="styles/style.css">`

Dentro de un subdirectorio llamado general, que está en un subdirectorio llamado styles, dentro del directorio actual

`<link rel="stylesheet" href="styles/general/style.css">`

Suba un nivel de directorio, luego dentro de un subdirectorio llamado estilos

`<link rel="stylesheet" href="../styles/style.css">`

### Hoja de estilo interna

Una hoja de estilo interna reside dentro de un documento HTML. Para crear una hoja de estilo interna, coloca codigo CSS dentro de un elemento `<style>` contenido dentro del HTML `<head>`.

El `HTML` de una hoja de estilo interna podría verse así:

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My CSS experiment</title>
    <style>
      h1 {
        color: blue;
        background-color: yellow;
        border: 1px solid black;
      }

      p {
        color: red;
      }
    </style>
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>This is my first CSS example</p>
  </body>
</html>
```

> En algunas circunstancias, las hojas de estilo internas pueden resultar útiles. Pero para los sitios con más de una página, una hoja de estilo interna se convierte en una forma de trabajo menos eficiente. Para aplicar un estilo CSS uniforme a varias páginas utilizando hojas de estilo internas, debe tener una hoja de estilo interna en cada página web que utilizará el estilo. La penalización por eficiencia también se traslada al mantenimiento del sitio. Con CSS en las hojas de estilo internas, existe el riesgo de que incluso un simple cambio de estilo requiera ediciones en varias páginas web.

### Estilos en línea

Los estilos en línea son declaraciones CSS que afectan a un solo elemento `HTML`, contenido dentro de un atributo de estilo. La implementación de un estilo en línea en un documento HTML podría verse así:

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My CSS experiment</title>
  </head>
  <body>
    <h1 style="color: blue;background-color: yellow;border: 1px solid black;">Hello World!</h1>
    <p style="color:red;">This is my first CSS example</p>
  </body>
</html>
```

> Se debe evitar usar CSS de esta manera, cuando sea posible. Primero, es la implementación menos eficiente de CSS para el mantenimiento. Un cambio de estilo puede requerir múltiples ediciones dentro de una sola página web. En segundo lugar, CSS en línea también mezcla código de presentación (CSS) con HTML y contenido, lo que hace que todo sea más difícil de leer y comprender. La separación de código y contenido facilita el mantenimiento para todos los que trabajan en el sitio web.

> Hay algunas circunstancias en las que los estilos en línea son más comunes. Puede que tenga que recurrir al uso de estilos en línea si su entorno de trabajo es muy restrictivo. Por ejemplo, quizás su CMS solo le permita editar el cuerpo HTML. También puede ver muchos estilos en línea en el correo electrónico HTML para lograr la compatibilidad con tantos clientes de correo electrónico como sea posible.

## Sintaxis CSS

CSS es un lenguaje basado en reglas, se definen reglas que especifican grupos de estilos que deben aplicarse a elementos particulares o grupos de elementos en su página web. Por ejemplo

```
h1 {
  color: red;
  font-size: 5em;
}
```

La regla abre con un `selector`. Esto selecciona el elemento HTML que vamos a diseñar. En este caso, estamos diseñando títulos de nivel uno `<h1>`.

Luego tenemos llaves `{}`. Dentro de ellos habrá una o más declaraciones, que toman la forma de pares de **propiedad** y **valor**. Cada par especifica una propiedad de los elementos que estamos seleccionando, luego un valor que nos gustaría darle a la propiedad.

Antes de los dos puntos, tenemos la propiedad, y después de los dos puntos, el valor. Las propiedades CSS tienen diferentes valores permitidos, según la propiedad que se especifique. En nuestro ejemplo, tenemos la propiedad color, que puede tomar varios valores de color. También tenemos la propiedad font-size. Esta propiedad puede tomar varias unidades de tamaño como valor.

Una hoja de estilo CSS contendrá muchas de estas reglas, escritas una tras otra. Ejemplo

```
h1 {
  color: red;
  font-size: 5em;
}

p {
  color: black;
}
```

### Selectores

Un selector apunta a HTML para aplicar estilos al contenido. Cada regla CSS comienza con un selector, o una lista de selectores, para indicarle al navegador a qué elemento o elementos se deben aplicar las reglas. Todos los ejemplos siguientes son selectores válidos o listas de selectores.

```
h1
a:link
.manythings
#onething
*
.box p
.box p:first-child
h1, h2, .intro
```

### Especificidad

Puede encontrar situaciones en las que dos selectores seleccionan el mismo elemento HTML. Considere la hoja de estilo a continuación, con un selector `p` que establece el texto del párrafo en `azul`. Sin embargo, también hay una `clase` que establece el texto de los elementos seleccionados en `rojo`.

```
.special {
  color: red;
}

p {
  color: blue;
}
```

Suponga que en un documento `HTML`, tenemos un párrafo con una `clase` de especial. Se aplican ambas reglas. ¿Qué selector prevalece? ¿Espera ver un texto de párrafo azul o rojo?

`<p class="special">What color am I?</p>`

El lenguaje CSS tiene reglas para controlar qué selector es más fuerte en caso de conflicto. Estas reglas se denominan cascada y especificidad. En el bloque de código a continuación, definimos dos reglas para el selector `p`, pero el texto del párrafo será azul. Esto se debe a que la declaración que establece el texto del párrafo en azul aparece más adelante en la hoja de estilo. Los estilos posteriores reemplazan los estilos en conflicto que aparecen anteriormente en la hoja de estilo. Esta es la regla de la cascada.

```
p {
  color: red;
}

p {
  color: blue;
}
```

Sin embargo, en el caso de nuestro ejemplo anterior con el conflicto entre el selector de clases y el selector de elementos, la clase prevalece, haciendo que el texto del párrafo sea rojo. ¿Cómo puede suceder esto a pesar de que aparece un estilo conflictivo más adelante en la hoja de estilo? Una clase se clasifica como más específica, como tener más especificidad que el selector de elementos, por lo que cancela la otra declaración de estilo en conflicto.


## Empezando con CSS

### Añadiendo CSS a un documento

Para vincular una hoja de estilo css como `styles.css` a un documento como `index.html`, se agrega la siguiente línea en algún lugar dentro del `<head>` del documento HTML:

```
<link rel="stylesheet" href="styles.css">
```

### Añadiendo la etiqueta `<style>` en el elemento `<head>` de un documento HTML

```
<style>
  body {
    background-color: tomato;
  }
</style>
```

### Añadiendo el atributo `style` en alguna etiqueta del documento HTML

```
<a href="https://shop.pimoroni.com/" style="color: goldenrod;">pimoroni</a>
```

Podemos apuntar y diseñar un elemento HTML. Hacemos esto apuntando a un selector de elementos

```
p {
  color: green;
}
```

Se puede apuntar a varios selectores a la vez

```
p, li {
  color: green;
}
```

### El atributo `class`

Dar estilo a elementos especificos

Dado el siguiente HTML

```
<ul>
  <li>Item one</li>
  <li class="special">Item two</li>
  <li>Item <em>three</em></li>
</ul>
```

Y el siguiente CSS

```
.special {
  color: orange;
  font-weight: bold;
}
```

### Aplicar estilo a las cosas según su ubicación en un documento

```
li em {
  color: rebeccapurple;
}
```

### Combinador de hermanos adyacentes

```
h1 + p {
  font-size: 200%;
}
```

### Diseñar cosas según el estado

Otro tipo de estilo es que da la capacidad de diseñar cosas según su estado. Un ejemplo sencillo de esto es el estilo de enlaces. Cuando le damos estilo a un enlace, necesitamos apuntar al elemento `<a>` (ancla). Esto tiene diferentes estados dependiendo de si no se visita, se visita, se desplaza, se enfoca a través del teclado o en el proceso de hacer clic (activar). Puede usar CSS para apuntar a estos diferentes estados: el CSS a continuación aplica un estilo a los enlaces no visitados en rosa y los enlaces visitados en verde.

```
a:link {
  color: pink;
}

a:visited {
  color: green;
}
```

Puede cambiar la apariencia del enlace cuando el usuario pasa el mouse sobre él, por ejemplo, eliminando el subrayado, lo que se logra en la siguiente regla:

```
a:hover {
  text-decoration: none;
}
```

### Combinando selectores y combinadores

Señalar que puede combinar múltiples selectores y combinadores juntos, Por ejemplo:

Selecciona cualquier `<span>` que esté dentro de un `<p>`, que esté dentro de un `<article>`

```article p span { ... }```

Selecciona cualquier `<p>` que viene directamente después de un `<ul>`, que viene directamente después de un `<h1>`

```h1 + ul + p { ... }```

También puede combinar varios tipos juntos.

Por ejemplo, aplique estilo a cualquier elemento con una clase de especial, que está dentro de un `<p>`, que viene justo después de un `<h1>`, que está dentro de un `<body>`. ¡Uf!

```
body h1 + p .special {
  color: yellow;
  background-color: black;
  padding: 5px;
}
```

# El modelo de caja

En CSS, en general, hay dos tipos de cajas: **cajas de bloque** y **cajas en línea**. Estas características se refieren a cómo se comporta el cuadro en términos de flujo de página y en relación con otros cuadros de la página:

Si una caja se define como un bloque, se comportará de las siguientes formas:

- La caja se termina en una nueva línea.
- La caja se extenderá en la dirección en línea para llenar el espacio disponible en su contenedor. En la mayoría de los casos esto significa que la caja será tan ancha como su contenedor, llenando el 100% del espacio disponible.
- Se respetan los valores de las propiedades de ancho y alto.
- El relleno, el margen y el borde harán que otros elementos se alejen del cuadro.

A menos que decidamos cambiar el tipo de visualización a en línea, elementos como los `<h1>`, `<div>` y `<p>` todos usan bloque como su tipo de visualización exterior de forma predeterminada.

Si una caja tiene un tipo de pantalla exterior en línea, entonces:

- La caja no se romperá en una nueva línea.
- Las propiedades de ancho y alto no se aplicarán.
- Se aplicarán el relleno, los márgenes y los bordes verticales, pero no harán que otros cuadros en línea se alejen del cuadro.
- Se aplicarán el relleno horizontal, los márgenes y los bordes y harán que otros cuadros en línea se alejen del cuadro.

El elemento `<a>`, utilizado para los enlaces, `<span>`, `<em>` y `<strong>` son todos ejemplos de elementos que se mostrarán en línea de forma predeterminada.

> El tipo de caja que se aplica a un elemento se define mediante valores de propiedad de `display`, como bloque y en línea, y se relaciona con el valor exterior de visualización.

## ¿Qué es el modelo de caja CSS?

El modelo de caja CSS completo se aplica a las cajas de bloque, las cajas en línea solo usan parte del comportamiento definido en el modelo de caja. El modelo define cómo las diferentes partes de un cuadro (margen, borde, relleno y contenido) trabajan juntas para crear un cuadro que se puede ver en la página.

### Partes de la caja

El siguiente diagrama muestra las capas:

![box model](./box-model.png)

## El modelo de caja CSS estándar

En el modelo de caja estándar, si se da a una caja un atributo de ancho y alto, esto define el ancho y la altura del cuadro de contenido. Luego, cualquier relleno y borde se agrega a ese ancho y alto para obtener el tamaño total que ocupa la caja.

De esta forma

```
.box {
  width: 350px;
  height: 150px;
  margin: 10px;
  padding: 25px;
  border: 5px solid black;
}
```

El espacio que ocupará esta caja usando el modelo de caja estándar será en realidad 410px (350 + 25 + 25 + 5 + 5) y la altura 210px (150 + 25 + 25 + 5 + 5), ya que el relleno y el borde son añadido al ancho utilizado para el cuadro de contenido.

## Utilice DevTools del navegador para ver el modelo de caja

Las herramientas de desarrollo de su navegador pueden facilitar la comprensión del modelo de caja. Si inspecciona un elemento en DevTools de por ejemplo Firefox, puede ver el tamaño del elemento ademas de su margen, relleno y borde. 


![box model devtools](./box-model-devtools.png)

## Márgenes, relleno y bordes

Exploremos estas propiedades con más detalle.

### Márgenes

El margen es un espacio invisible alrededor de una caja. Empuja otros elementos fuera de la caja. Los márgenes pueden tener valores positivos o negativos. Establecer un margen negativo en un lado de su cuadro puede hacer que se superponga con otras cosas en la página.

Podemos controlar todos los márgenes de un elemento a la vez usando la propiedad `margin`, o cada lado individualmente usando las propiedades equivalentes a mano:


- [margin-top](https://developer.mozilla.org/en-US/docs/Web/CSS/margin-top)
- [margin-right](https://developer.mozilla.org/en-US/docs/Web/CSS/margin-right)
- [margin-bottom](https://developer.mozilla.org/en-US/docs/Web/CSS/margin-bottom)
- [margin-left](https://developer.mozilla.org/en-US/docs/Web/CSS/margin-left)

### Relleno

El relleno se encuentra entre el borde y el área de contenido. A diferencia de los márgenes, no puede tener cantidades negativas de relleno, por lo que el valor debe ser 0 o un valor positivo.

Podemos controlar el relleno en cada lado de un elemento individualmente usando la propiedad [padding](https://developer.mozilla.org/en-US/docs/Web/CSS/padding), o cada lado individualmente usando las propiedades individuales equivalentes:

- [padding-top](https://developer.mozilla.org/en-US/docs/Web/CSS/padding-top)
- [padding-right](https://developer.mozilla.org/en-US/docs/Web/CSS/padding-right)
- [padding-bottom](https://developer.mozilla.org/en-US/docs/Web/CSS/padding-bottom)
- [padding-left](https://developer.mozilla.org/en-US/docs/Web/CSS/padding-left)

### Borde

El borde se dibuja entre el margen y el relleno de un cuadro. Si está utilizando el modelo de caja estándar, el tamaño del borde se agrega al ancho y alto de la caja. Si está utilizando el modelo de cuadro alternativo, el tamaño del borde hace que el cuadro de contenido sea más pequeño, ya que ocupa parte del ancho y alto disponibles.

Para dar estilo a los bordes, hay una gran cantidad de propiedades: hay cuatro bordes y cada borde tiene un estilo, ancho y color que tal vez queramos manipular.

Se puede establecer el ancho, el estilo o el color de los cuatro bordes a la vez utilizando la propiedad [borde](https://developer.mozilla.org/en-US/docs/Web/CSS/border).

Para establecer las propiedades de cada lado individualmente, puede usar:

- [border-top](https://developer.mozilla.org/en-US/docs/Web/CSS/border-top)
- [border-right](https://developer.mozilla.org/en-US/docs/Web/CSS/border-right)
- [border-bottom](https://developer.mozilla.org/en-US/docs/Web/CSS/border-bottom)
- [border-left](https://developer.mozilla.org/en-US/docs/Web/CSS/border-left)

Para establecer el ancho, estilo o el color de todos los lados, puede usar:

- [border-width](https://developer.mozilla.org/en-US/docs/Web/CSS/border-width)
- [border-style](https://developer.mozilla.org/en-US/docs/Web/CSS/border-style)
- [border-color](https://developer.mozilla.org/en-US/docs/Web/CSS/border-color)

Para establecer el ancho, el estilo o el color de un solo lado, puede usar una de las propiedades individuales:

- [border-top-width](https://developer.mozilla.org/en-US/docs/Web/CSS/border-top-width)
- [border-top-style](https://developer.mozilla.org/en-US/docs/Web/CSS/border-top-style)
- [border-top-color](https://developer.mozilla.org/en-US/docs/Web/CSS/border-top-color)
- [border-right-width](https://developer.mozilla.org/en-US/docs/Web/CSS/border-top-color)
- [border-right-style](https://developer.mozilla.org/en-US/docs/Web/CSS/border-right-style)
- [border-right-color](https://developer.mozilla.org/en-US/docs/Web/CSS/border-right-color)
- [border-bottom-width](https://developer.mozilla.org/en-US/docs/Web/CSS/border-bottom-width)
- [border-bottom-style](https://developer.mozilla.org/en-US/docs/Web/CSS/border-bottom-style)
- [border-bottom-color](https://developer.mozilla.org/en-US/docs/Web/CSS/border-bottom-color)
- [border-left-width](https://developer.mozilla.org/en-US/docs/Web/CSS/border-left-width)
- [border-left-style](https://developer.mozilla.org/en-US/docs/Web/CSS/border-left-style)
- [border-left-color](https://developer.mozilla.org/en-US/docs/Web/CSS/border-left-color)

## Bloque en línea

Existe un valor especial de visualización, que proporciona un término medio entre `inline` y `block`. Es útil para situaciones en las que no desea que un elemento salte a una nueva línea, pero desea que respete el ancho y la altura y evite la superposición.

Un elemento con `display: inline-block` hace que un subconjunto del bloque cosas que ya conocemos:

- Se respetan las propiedades `width` y `height`.
- `padding`, `margin` y `border` provocarán que otros elementos se alejen del cuadro.

Sin embargo, no se salta a una nueva línea.




