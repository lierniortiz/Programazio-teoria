# CSS

Para aplicar estilos a los elementos HTML. Veremos las hojas de estilo en cascada.

Extensiones para Visual Studio Code: 

* 


Para añadir la hoja de estilo al HTML ver el apartado link de metadata en el apartado de HTML. 

¿Cómo se define el estilo de un elemento?

```
selector{
    propiedad1: valor1;
    propiedad2: valor2;
    ...
}
```

Se llama en cascada porque el último selector que escribas es el que lea el HTML. Por ejemplo en,

```
h1{
    color: blue;
}

h1{
    color: red;
}
```

aunque `h1` esté repetido, para el HTML será rojo, porque es el último que hemos escrito en el CSS. Esto pasará siempre que sean de la misma jeraquía (ver especifidad).

Pasa lo mismo si cargáramos dos hojas de estilo en la metadata del HTML. La última hoja de estilo que hayamos escrito será la que cargue última, por tanto sobreescribirá la primera hoja de estilo si hay selectores repetidos. 

## Inspector de google chrome

Es interesante utilizar la inspección de chrome para cambiar cosas en el momento y luego traerlas a nuestro documento.

Si nos ponemos en elements, encima del que queremos darle estilo y luego vamos a styles, aparecerá un `+` arriba a la derecha y automáticamente nos dirá el estilo de qué estamos cambiando.

Una vez ahí, si nos ponemos encima de la medida con la que estamos trabajando y le damos a las flechas iremos cambiando poco a poco.

En el editor se pueden activar y desactivar propiedades. Si las copiamos y pegamos con algunas desactivadas se nos coparán a nuestro editor como un comentario.

## Selectores

### Universal

```
*{
    color: blue;
}
```

Se aplicará a todo el documento. Por ejemplo si especificamos el color, el color de todas las letras serán de esa forma hasta que se escriba lo contrario más adelante en el documento CSS.

### Selector de elementos
 Elementos de HTML: `p`, `div`...

```
p{
    color:black;
}


div{
    color: red;
}
```

### Selector por id
Cambiará el estilo solamente a aquel elemento que tenga este id. Recuerda que es único!

```
#nuestroid{
    color: yellow;
}
```

### Selector por clase
Afectará a todos los elementos que sean de esta clase. No son únicos, podemos tener tantos elementos con esta clase como queramos.
```
.nuestraclase{
    color: yellow;
}
```

### Por atributos
Nos podemos inventar atributos en el HTML. Por ejemplo:
```
HTML
<div atributo="hola">contenido</div>

CSS
[atributo="hola"]{
    color="blue"
}
```

No se utiliza. Este es el único:
```
input[type="text"] {
    border: 3px solid #000;
}
```
### Selector descendiente

```
HTML
<div class="div1>
    <p>Contenido
    </p>
</div>

<div class="div2>
    <p>Contenido
    </p>
</div>

CSS
.div1 p{
    color:blue
}
```

De esta forma no tenemos que identificar el párrafo uno a uno. Nos ahorra etiquetas. En el código de arriba el párrafo primero es hijo de `div1`, por eso es el que cambiamos con el CSS. Esto se utiliza mucho.

### Pseudoclases
```
.div1:hover{
    color: blue;
    cursor: pointer;
}
```
Cuando pasemos por encima con el ratón, el `div1` se convertirá azul y se nos pondrá la manita en vez de la flechita.

```
.div1:focus{
    color: blue;
    cursor: pointer;
}
```

### Agrupar selectores

```
h1, h2, p {
    color: pink;
}

```

## Especifidad

No siempre hay cascada porque hay una jerarquía entre elementos, una especifidad. El estilo de algunos elementos tendrá más importancia que otros independientemente al orden en el que están.

Aquí estan de más importante a menos importante:

`!important > estilos en linea > identificadores > clases/pseudo-clases/atributos > elementos > pseudoelementos`


* PSEUDOELEMENTOS. No se suelen utilizar mucho. [Link: Pseudo-elements](https://www.w3schools.com/css/css_pseudo_elements.asp)

* ELEMENTOS. Son los elementos de HTML, como `<p>`, `<div>`... No suelen usarse para el estilo, porque se sobreescribirá en seguida.

* CLASES/ATRIBUTOS. Están en el mismo nivel.

* IDENTIFICADORES. id que le hemos puesto al elemento. Seguramente no vayas a sobreescirbirlo. Pero el inconveniente es que solo habrá un elemento con ese id, entonces habrá que darle estilo muchas veces.

* ESTILOS EN LINEA. Darle el atributo `style=" "` en la hoja HTML. La hoja de estilos no tendrá nada que decir ante esto.

* `!important` es conveniente no utilizarlo, sobreescribe a todos los demás. A veces no queda más remedio. Después van en orden. Los que van antes en esa lista sobreescribirán a los siguientes. Funciona así:
```
.verde{
    color: green!important;
}
```

EN EL INSPECTOR DE CHROME

Podemos ver los estilos que están aplicados si nos ponemos encima de nuestro elemento. Los tachados no se están aplicando a ese elemento. También se puede ver los que se aplican por defecto.

En computed, se puede ver de donde viene el estilo que tiene.


### Metodología bem

Evita conflictos de espeficidad. Es una nomenclatura basada en clases.

Se utilizan __ para los hijos de los elementos y -- por si algún hijo es diferente. 

`clase del padre__clase del hijo--caracteristica especial del hijo`

```
<form class="contact-form">
    <input type="text" class="contact-form__input" name="nombre">
    <input type="text" class="contact-form__input contact-form__input--active"  name="email">
    <button type="submit"  class="contact-form__button" ></button>
</form>

<form class="login-form">
    <input type="text" class="login-form__input" >
    <input type="password"  class="login-form__input login-form__input--password">
    <button type="submit" class="login-form__button"></button>
</form>
```


## Fuentes

[Fuentes de google](https://fonts.google.com/)

Elegimos la que queramos, seleccionamos y le damos a `select this style` a tantas fuentes como queramos. A la derecha nos aparecerá un texto y lo copiamos a la cabecera en la metadata de HTML. Además, en el CSS haremos lo siguiente:

```
body{
    font-family: la que nos ha dicho google a la derecha
    font-size: 16px;
    list-style: 20px;
    font-weight: 500;
}
```
De esta forma habremos especificado el tipo de letra para todo el documento.

Para asegurarnos que la fuente que hemos elegido esté disponible en todos los dispositivos:
[Web safe fonts](https://www.w3schools.com/cssref/css_websafe_fonts.asp)

## Colores
Si escribimos `blue`, `red`... estamos dejando la interpretacion al navegador.

Podemos ponerlo en rgb o hexadecimal. En VSC podemos ponernos encima del cuadradito de color y elegir color y opacidad.

### Opacidad

...

## Posiciones

### Comportamiento de elementos

Dos maneras de comportarse:

* Elementos de bloque: cogen todo el espacio horizontal. Por ejemplo: `<div>`
* Elementos de linea: que se ajustan al contenido. Por ejemplo: `<a>` 

Podemos cambiar el comportamiento con `display:block`, `display:inline`.

Hay propiedades que uno u otro no aceptan, por ejemplo los elementos en linea no aceptan tener diferente altura.

Podemos cambiar a 4 tipo de posiciones:

* Absoluta. `position: absolute` Para que un elemento siempre esté en un sitio fijo.
* Relativa. `position: relative` Para cambiar un poco a nuestro gusto.
* Fija. `position: fixed` Para que aunque vayamos arriba y abajo con el scroll se quede en la misma posición. 
* Pegajosa. `position: sticky`

### Overflow

Si el contenido es más grande que el contenido. No debería pasar nunca. Para ello

* `overflow: scroll;` scroll arriba-abajo e izquierda-derecha
* `overflow: auto;` scroll necesario (puede ser solo arriba-abajo pero no izquiera-derecha)
* `overflow: hidden;` Que no se muestre la parte que sobresale del contenedor

En las imagenes es raro utilizar esta propiedad, para que no se salga del contenedor lo que se suele hacer es especificar la anchura máxima como:

* `max-width: 100%` Nunca ocupará más del 100% del contenedor.

### Flexbox

TOTALMENTE RECOMENDADO UTILIZAR

Si queremos cajas ordenadas de forma simetrica, o de arriba abajo, o con ciertas propiedades...

Con darle `display: flex` al contenedor los elementos hijos de ese contenedor se colocarán de la forma que decida el navegador. Es muy fácil utilizar esto por que responden muy bien al responsive. Suele mantener el espacio máximo del contenedor a no ser que estemos en otro dispositivo donde necesitan ser más pequeñitos.

Los navegadores están adecuandose a esto y dando facilidades para ello. Si vamos al inspector en styles aparece un iconito al lado de `flex` y se pueden cambiar las propiedades desde ahí.

## Galería de imágenes

Hacer una galería con html y css sin js o php. Aparecen y desaparecen imágenes. Hay debate si sobre es programación o maquetación.

[GitHub-html de galería](https://github.com/lierniortiz/Programazio-teoria/blob/main/css/galeria.html)

[GitHub-css de galería](https://github.com/lierniortiz/Programazio-teoria/blob/main/css/galeria.css)

## Ejemplo de un formulario

HTML

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link href="css/form.css" type="text/css" rel="stylesheet">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Open+Sans&family=Roboto:wght@500&display=swap" rel="stylesheet">

</head>
<body>
    <div class="contenedor">
        <div class="login-form">
          <form>
            <h1>Login form</h1>
            <div class="login-form__field">
            <input type="text" name="usuario" id="usuario" required class="login-form__field--usuario" placeholder="Usuario" />
            </div>
            <div class="login-form__field">
                <input type="password" name="password" id="password" required  class="login-form__field--password" placeholder="Password" />
            </div>
            <div class="login-form__field">
                <input type="checkbox" name="check" id="check" class="login-form__field--checkbox" /><label for="check">He leído y acepto la política de privacidad</label>
            </div>

            <div class="login-form__button">
                <button type="submit" class="login-form__button--button">Enviar</button>
            </div>


          </form>
        </div>
      </div>

</body>
</html>
```
CSS
```
html, body {
    margin:0; 
  }
  
  body {
    background-image:url(spaghetti.webp);
    background-size: cover;
    background-attachment: fixed;
    background-position: center;
    font-family: 'Roboto';
  }

  .contenedor {
      display: flex;
      position: absolute;
      width: 100%;
      height: 100%;
      flex-direction: column;
      justify-content: center;
      align-items: center;
  }
  
  .login-form {
      background-color: #fff;
      max-width: 400px;
      padding: 30px;
      border-radius: 10px;
      margin: 20px;
  }

  .login-form__field {
    margin-bottom: 10px;
}

.login-form__field input {

    width: 230px;
    max-width: 100%;
    height: 30px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 18px;

}

input#usuario {
    background: transparent;
    background-image: url(user.png);
    background-repeat: no-repeat;
    background-position: 3px;
    padding-left: 30px;
}

input#password {
    background: transparent;
    background-image: url(key.png);
    background-repeat: no-repeat;
    background-position: 3px;
    padding-left: 30px;
}

input#check {
    width: auto;
    height: 20px;
    width: 20px;
}

h1 {
    font-family: 'Open Sans';
}

button.login-form__button--button {
    background-color: #0db6f0;
    border: 0;
    padding: 10px;
    margin-top: 20px;
    font-size: 18px;
    font-family: 'Roboto';
    color: #fff;
}

[for="check"] {
    font-size: 13px;
    position: relative;
    top: -5px;
    margin-left: 7px;
}
```

### Explicación del ejemplo

**1) `html` y `body` quitar margenes.**


**2) Dar una imagen de fondo al `body`**

```
 body {
    background-image:url(spaghetti.webp);
    background-size: cover;
    background-attachment: fixed;
    background-position: center;
    font-family: 'Roboto';
  }
```
Para que la imagen se vea siempre bien `background-size: cover;` y `background-attachment: fixed;`. De esta forma la imagen llenará toda la pantalla. Se adaptará a ella de manera inteligente.

Además con `background-position: center;` siempre guardará el centro de la imagen en el centro con responsive.

Se puede jugar con la imagen con `background-blend-mode: propiedad;` y darle un `background-color` a la imagen. 

**3) Alineación**.

Queremos que el contenedor contenga el formulario esté siempre alineado en medio tanto horizontalmente como verticalmente y ocupando todo. Y que sus elementos hijos estén alineados de igual manera, es decir que el formulario siempre esté en medio.
```
  .contenedor {
      display: flex;
      position: absolute;
      width: 100%;
      height: 100%;
      flex-direction: column;
      justify-content: center;
      align-items: center;
  }
```
Las tres últimas propiedades, lo más fácil es hacerlo mediante el inspector de google, ya que nos brinda interfaz.

**4) Creamos otro contenedor, que será el que contenga el formulario.**

```
<div class="login-form">
    ...
</div>

```

```
.login-form {
      background-color: #fff;
      max-width: 400px;
      padding: 30px;
      border-radius: 10px;
      margin: 20px;
  }
```
**5) Fuentes.**
```
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=Open+Sans&family=Roboto:wght@500&display=swap" rel="stylesheet">
```
Cambia el grosor según los píxeles del dispotisivo donde estemos. (?)

**6) Elementos del formulario.**

Las clases siguen la metodología bem (ver especifidad). 

Los campos del formulario. `login-form__field input`:
```
.login-form__field input {

    width: 230px;
    max-width: 100%;
    height: 30px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 18px;

}

```

Con esto el check-box también tiene esa anchura, pero no nos conviene. Por tanto:

```
input#check {
    width: auto;
    height: 20px;
    width: 20px;
}

```
Esta no es la forma correcta de hacerlo. Deberíamos haber aplicado el estilo solo a los campos que lo necesiten. Pero de esta forma repasamos la especifidad viendo que los id-s ganan a las clases. 

Además, para el checkbox creamos un atributo específico para él, ya que será un poco diferente a los demás campos.
```
<div class="login-form__field">
                <input type="checkbox" name="check" id="check" class="login-form__field--checkbox" /><label for="check">He leído y acepto la política de privacidad</label>
            </div>
```

```
[for="check"] {
    font-size: 13px;
    position: relative;
    top: -5px;
    margin-left: 7px;
}
```
**7) Botón.**

```
button.login-form__button--button {
    background-color: #0db6f0;
    border: 0;
    padding: 10px;
    margin-top: 20px;
    font-size: 18px;
    font-family: 'Roboto';
    color: #fff;
}
```

Los botones tienen su propia fuente por defecto. Hay que especificarle siempre cual queremos por esa razón (?). Si tenemos duda de si lo estamos aplicando vamos al inspector a compute. 

**8) Usuario y contraseña.**

Como usuario y password también son un poco diferentes hacemos lo siguiente:
```
input#usuario {
    background: transparent;
    background-image: url(user.png);
    background-repeat: no-repeat;
    background-position: 3px;
    padding-left: 30px;
}

input#password {
    background: transparent;
    background-image: url(key.png);
    background-repeat: no-repeat;
    background-position: 3px;
    padding-left: 30px;
}
```

## Bootstrap
Es un framework (un conjunto estandarizado de conceptos, prácticas y criterios para enfocar un tipo de problemática) para trabajar estilos en CSS y JS. Actualmente vamos por la versión 5. Sirve para cosas que se mueven: acordeones, carruseles, diseños adaptativos... Pero también para dar estilos de forma estandarizada y sencilla.

En su página podemos ver todos los estilos de diferentes elementos y cómo utilizarlos: [bootstrap.com](https://getbootstrap.com)

Se puede instalar con un modulo de NodeJS.

De momento lo haremos con el código que ellos nos dan en [bootstrap.com](https://getbootstrap.com/docs/5.1/getting-started/introduction/):

```
<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">

    <title>Hello, world!</title>
  </head>
  <body>
    <h1>Hello, world!</h1>

    <!-- Optional JavaScript; choose one of the two! -->

    <!-- Option 1: Bootstrap Bundle with Popper -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>

    <!-- Option 2: Separate Popper and Bootstrap JS -->
    <!--
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.10.2/dist/umd/popper.min.js" integrity="sha384-7+zCNj/IqJ95wo16oMtfsKbZ9ccEh31eOz1HGyDuCQ6wgnyJNSYdrPa03rtR1zdB" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.min.js" integrity="sha384-QJHtvGhmr9XOIpI6YVutG+2QOK9T+ZnN4kzFN1RtK3zEFEIsxhlmWl5/YESvpZ13" crossorigin="anonymous"></script>
    -->
  </body>
</html>
```

Trabajando más con cdn-s vamos a "robar" el estilo de la página de booststrap misma. Para ello iremos a [layout > grid](https://getbootstrap.com/docs/5.1/layout/grid/), inspeccionamos el código de las tres columnas y vemos que el estilo de eso está en una hoja de estilo que se llama `docs.css`. Clicamos encima con el botón derecho y `Open in new tab`. Podemos copiar todo el texto y crear una hoja de estilos nueva con ese texto. 

### Ejemplo de grid

```
<html lang="es">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
    <link href="css/docs2.css" rel="stylesheet" type="text/css">

    <title>Hello, world!</title>
  </head>
  
  <body>
    <h1>Hello, world!</h1>


<!-- responsive clases-->

     <div class="bd-example bd-example-row">
        <div class="container">
            <div class="row">   
              <div class="col-sm-4">col-sm-6</div>
              <div class="col-sm-8">col-sm-6</div>
            </div>
            <div class="row">
              <div class="col-sm">col-sm</div>
              <div class="col-sm">col-sm</div>
              <div class="col-sm">col-sm</div>
            </div>
    </div>

```

Con las dos hojas de estilo que nos hemos traído antes, la de bootstrap y la "robada", si ahora escribimos eso ya nos aparece con estilo dado. Hay que saberse el nombre de las clases, por ejemplo en estas `col-sm-4` y `col-sm-8` entre las dos tiene que sumar 12 (podía ser 6 y 6) tal y como podemos ver en el apartado "Grid options" de la [página de booststrap](https://getbootstrap.com/docs/5.1/layout/grid/). Estas columnas que hemos creado se irán comportando de una forma u otra según los px del dispositivo. 

## Animaciones

Una librería para animaciones: [animate.style](https://animate.style/)

Al igual que con booststrap también hay que cargar la biblioteca de animate como se dice en la web. Se puede con `npm`, pero también se puede cargar añadiendo el cdn al documento html:
```
<head>
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css"
  />
</head>

```

En la página web hay un menú con todas las animaciones posibles y cómo usarlas. 

También se puede acudir a [w3schoow](https://www.w3schools.com/css/css3_animations.asp)

Siempre tienen un elemento de partida y un elemento de destino. Además entre elementos podemos poner hitos intermedios (en porcentajes). Ejemplo: 

```
/*
animation-name
animation-duration
animation-delay
animation-iteration-count
animation-direction
animation-timing-function
animation-fill-mode
*/

.midiv:hover, .midiv.active {
    animation-name: ejemplo2;
    animation-duration: 1s;
    animation-timing-function:ease-in;
    animation-fill-mode:forwards;
    animation-iteration-count:infinite;
}


  @keyframes ejemplo2 {
    10% {
        background-color: red;
        transform: rotate(0deg);}
    50% {background-color: yellow;
        transform: rotate(45deg);}
    100% {background-color: rgb(10, 10, 1);
        transform: rotate(180deg);}
  }
```

### Transiciones

Nuestro objetivo es que no haya transiciones bruscas. Por ejemplo, cuando ponemos el ratón encima de un botón y que cambie de color, que este cambio no sea brusco.

Hoja de referencia de [w3school](https://www.w3schools.com/css/css3_transitions.asp) donde se dicen los estándares.

```
HTML
-----------------------------------------------------------

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <link href="css/transiciones.css" rel="stylesheet" type="text/css">
</head>
<body>

<div class="contenedor">
    <button class="btn">Mi transición</button>
    <div class="midiv"></div>
</div>

</body>
</html>
```

```
CSS
-------------------------------------------------------------

.contenedor {
    display: flex;
    position: absolute;
    width: 100%;
    height: 100%;
    left: 0;
    top: 0;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

button.btn {
    height: 50px;
    border:0;
    width: 300px;
    background-color: blue;
    color: white;
    font-size: 20px;
    font-family: Arial, Helvetica, sans-serif;
    transition-duration: 3s;
    transition-delay:1s;
    transition-timing-function: ease;
    transition-property:all;
    transition: all 2s ease 1s;
  
}

button.btn:hover {
    background-color: tomato;
    color:black;
    transform: translate(100px);
    cursor:pointer;
    transition: all 2s ease;
}

.midiv {
    height: 160px;
    background-color: black;
    width: 290px;
    margin-top: 30px;
    transition: all 1s ease-in;
}

.midiv:hover, .midiv.active {
    transition: all 1s ease-out;
    transform: matrix(1, -0.2, 0, 1, 0, 0);
    background-color: blueviolet;
    height: 300px;
    width: 500px;
}

```

- `transition` es la que nos ayuda en la transición. Fijarse en que tenemos la transición en el botón y en el `:hover`
    * `transition: all`
    * `transition: background-color`
    * `transition-delay`
    * `transition-duration`
    * `transition-timing-function`
    * ... ver más en el [link](https://www.w3schools.com/css/css3_transitions.asp). 

* También podemos hacer transiciones con los div. 
* Combinamos las clases `:hover` y `active` para que los dos tengan la misma animación. 
* Podemos ver curvas de animación en: [easings.net](https://easings.net/). 

### Elementos que aparecen y desaparecen

Queremos simular mediante una transiciones que aparezcan o desaparezcas elementos. Por ejemplo el menú.

```
.menu {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: #000;
    color: #fff;
    opacity: 0;
    visibility: hidden;
    font-size: 40px;
    font-family: Arial, Helvetica, sans-serif;
    transition: all 2s ease-out;
}

.menu.active {
    opacity: 1;
    visibility:visible;
    transition: all 2s ease-in;
}
```

Hemos especificado que el menú por defecto es `hidden` y `opacity: 0;`. Si la clase se vuelve active tenemos `opacity: 1;` y  `visibility:visible;`. El cambio de añadir una nueva clase se hará desde javascript. Es la forma de enseñar elementos que están ocultos en la web. 

### Ejemplo de spinner
Podemos convinar animaciones y transiciones. Ejemplo de spinner:

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link href="css/rotando.css" rel="stylesheet" type="text/css">
</head>
<body>

    <div class="contenedor">
     <svg class="misvg" xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 0 24 24" width="24px" fill="#000000"><path d="M0 0h24v24H0z" fill="none"/><path d="M12 6v3l4-4-4-4v3c-4.42 0-8 3.58-8 8 0 1.57.46 3.03 1.24 4.26L6.7 14.8c-.45-.83-.7-1.79-.7-2.8 0-3.31 2.69-6 6-6zm6.76 1.74L17.3 9.2c.44.84.7 1.79.7 2.8 0 3.31-2.69 6-6 6v-3l-4 4 4 4v-3c4.42 0 8-3.58 8-8 0-1.57-.46-3.03-1.24-4.26z"/></svg> 
    </div>
</body>
</html>
```

```
.contenedor {
    display: flex;
    position: absolute;
    width: 100%;
    height: 100%;
    left: 0;
    top: 0;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.misvg {
    height: 50px;
    width: 50px;
    fill: #333;
    opacity: 0;
    visibility: hidden; 
    transition: all 0.5s ease-in;
}

.misvg.active {
    animation-name: rotando;
    animation-duration: 1s;
    animation-timing-function:linear;
    animation-iteration-count:infinite;
    opacity: 1;
    visibility:visible;
    transition: all 2s ease-in;
}

  @keyframes rotando {
    for {
        fill: #333;
        transform: rotate(0deg);}
    50% {fill: #999;}
    100% {fill: #333;
        transform: rotate(180deg);}
  }

```

### Ejemplos de animaciones

* [Ejemplo1-rata](https://codepen.io/psyloute/pen/mdmEYqq)
* [Ejemplo2-botones que se mueven](https://codepen.io/sanketbodke/pen/LYymbRq)
* [Ejemplo3-spinner](https://codepen.io/tigercodes/pen/ExXJvGJ)
* [Ejemplo4-desplazamientos](https://codepen.io/AKGD/pen/yvwQYZ)
* Tooltips

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link href="css/tooltips.css" rel="stylesheet" type="text/css">
</head>
<body>
    <div class="contenedor">
        <p>Lorem ipsum dolor sit <span class="tooltip" data-info="Este es el texto del tooltip">ábreme el tooltip</span> amet consectetur adipisicing elit. Est explicabo fugit quos, a voluptas animi laudantium consequatur voluptatibus magnam sed reprehenderit aliquam, cupiditate commodi non nihil accusantium, tempore molestias quod?</p>
    </div>
</body>
</html>
```
```
.contenedor {
    display: flex;
    position: absolute;
    width: 100%;
    height: 100%;
    left: 0;
    top: 0;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-size: 20px;
    font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
    font-weight: 100;
    padding: 100px;
}

span.tooltip::before {
    display: none; /* Lo ocultamos*/
    content: attr(data-info);
    color: white;
    font-size: 0.8em;
    padding: 2px 8px;
    background: rgba(0,0,0,0.8);
    border-radius: 5px;
    position: absolute; /* Lo posicionamos de modo absoluto dentro del span */
    top: 1.5em;
    left: 5px;
    min-width: 500px;
    z-index: 999;
}

span.tooltip:hover::before {
    display: block;
}

span{
    position: relative;
    font-weight: 700;
    background-color: yellow;
    cursor: pointer;
}

```
