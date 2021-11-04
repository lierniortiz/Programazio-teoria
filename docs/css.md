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

aunque `h1` esté repetido, para el HTML será rojo, porque es el último que hemos escrito en el CSS. Esto pasará siempre que sean de la misma jeraquía (ver jerarquía).

Pasa lo mismo si cargáramos dos hojas de estilo en la metadata del HTML. La última hoja de estilo que hayamos escrito será la que cargue última, por tanto sobreescribirá la primera hoja de estilo si hay selectores repetidos. 

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

### Agrupar selectores

```
h1, h2, p {
    color: pink;
}

```

## Fuentes

[Fuentes de google](https://fonts.google.com/)

Elegimos la que queramos, seleccionamos y le damos a `select this style`. A la derecha nos aparecerá un texto y lo copiamos a la cabecera en la metadata de HTML. Además, en el CSS haremos lo siguiente:

```
body{
    font-family: la que nos ha dicho google a la derecha
    font-size: 16px;
    list-style: 20px;
    font-weight: 500;
}
```
De esta forma habremos especificado el tipo de letra para todo el documento.

## Colores
Si escribimos `blue`, `red`... estamos dejando la interpretacion al navegador.

Podemos ponerlo en rgb o hexadecimal. En VSC podemos ponernos encima del cuadradito de color y elegir color y opacidad.