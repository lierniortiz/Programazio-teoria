# HTML

## Generalidades

* Es un lenguaje de marcado de hipertexto. 

* Los buscadores (robots de google) se fijan en si la estructura de HTML está bien escrita. Para ello podemos verificar nuestro código en: [Validator w3c](https://validator.w3.org/)

* No se considera un lenguaje de programación, es un lenguaje de interpretación. 

* Un documento HTML se sirve desde un servidor web. http y https son diferentes tipos de encriptación. (Google exige https). 

* HERRAMIENTAS: Visual Studio Code, [CodePen](https://codepen.io/), [Stackblitz](https://stackblitz.com/)

## Iniciar

* En Visual Studio Code escribiendo `!` y pulsando enter se abrirá un plantilla HTML. 

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```

* `Head` y `Body` tendrán que estar siempre. En head habrá instrucciones (metadata): para google, para guardar en caché... En body estará los elementos html. 

* Extensiones posibles para VSC: HTML Format, HTML Preview, HTML Snippets, HTML CSS Support. 

### Organizar el documento
Organizar el documento de forma ordenada. Para el lector. No hacen nada.
```
<main>      Parte principal de la web</main>
<article>	Artículo. Parte principal de un escrito (posts, mensaje en foros, comentario...)
<nav>	    Apartado de navegación (enlaces de secciones, categorías, etc...)
<header>    Cabecera visual de la página (logotipo, título, etc...). No confundir con <head>.
<footer>	Pie de página de una sección (o del documento completo).
<section>	Sección o grupo temático de contenido. No usar sólo para dar estilo.
<aside>	    Agrupación de contenido no relacionado con el tema principal del documento.
<address>	Agrupación con la información de contacto del autor del artículo o documento.
```

## Metadata

* `lang` Idioma. Si tenemos una web multidioma habrá que cambiar este apartado a cada página. 

* `charset="UTF-8"` Para que sea compatible cualquier símbolo. 

* `<title>` Es el título que se muestra en la pestaña. 

### meta

* `<meta name="viewport">` Para el responsive. 
 
* `<meta description=" ">` Es la que aparecerá en los buscadores. 

### link

- Página con un documento asociado. 
```
<link rel="alternate" href="document.pdf" type="application/pdf" />
```
- Páginas multidioma. 
```
<link rel="alternate" href="document-en.html" hreflang="en" />
```
- El icono que aparecerá al lado del nombre de la página en la pestaña. 
```
<link rel="icon" sizes="64x64" href="/favicon.png />
```
- Para buscadores:

    * `rel="canonical"` Dirección URL exacta que Google debería asociar al documento. 
    * `rel="prev"` Si tiene varias páginas el contenido que viene antes. 
    * `rel="next"` Si tiene varias páginas el contenido que viene después. 

- Hojas de estilo: 
```
<link rel="stylesheet" href="style.css" type="text/css" />
```

- Tenemos rel="author", "help", "search", "license". 

### Cabeceras

Para que se vea, se comparta bien en navegadores. 

```
<!-- twitter-->
<meta property="twitter:card" content="summary_large_image" />
<meta property="twitter:creator" content="@Manz" />
<meta property="twitter:title" content="Título" />
<meta property="twitter:description" content="Descripción" />
<meta property="twitter:image:src" content="URL_img.jpg" />

```

## Estructura-Etiqueta

La estructura de una etiqueta: 

```
<etiqueta atributo="valor">contenido</etiqueta>
```
### Atributos comunes
Un elemento puede tener muchos atributos. 

* `id` Identifica de manera ÚNICA a un elemento, solo podemeos tener una por página con ese id.  
* `class` Se puede asociar a todos los elementos que queremos que tengan el mismo estilo. 
* `translate`
* `title`
* `dir`
* `style`
* `href`
* `dir`

### Valores
Tres opciones:


* Conjunto finito de valores
* Valores libres
* Valores booleanos

### Encabezados
```
<h1>Título principal. </h1>  (Solo debe de haber uno).
<h2>Encabezado de nivel 2. Equivalente al tema del documento.</h2>
<h3>Encabezado de nivel 3. Equivalente a la sección de un tema.</h3>
<h4>Encabezado de nivel 4. Equivalente a un apartado de la sección.</h4>
<h5>Encabezado de nivel 5. Equivalente a un ejemplo del apartado.</h5>
<h6>Encabezado de nivel 6. Equivalente a un subapartado del ejemplo.</h6>

```

### Etiquetas de texto posibles

```
<p>
  <time datetime="2001-01-04">4 de Enero</time>
  <data value="ESDLA3">El retorno del Rey</data>
</p>

<strong>Fragmento de texto importante o palabras clave.
<em>	Fragmento de texto enfatizado respecto a la frase que lo contiene.
<mark>	Fragmento de texto resaltado, simulando estar marcado con rotulador amarillo.
<span>	Fragmento de texto sin significado (útil para seleccionar).
<cite>	Fragmento de texto con el título de un trabajo creativo: obras, libros...

<sup>   Superíndice (242).
<sub>   Subíndice (242).
<small> Anotaciones menores pequeñas puntualizaciones.
<br>
<time>  datetime	Indica una fecha/hora legible para humanos, con formato para máquinas opcional.
<data>  value	Información equivalente orientado a máquinas.
<code>  Fragmento de código fuente (en línea).
```

## Iframes

...

[GitHub-Iframes](https://github.com/lierniortiz/Programazio-teoria/blob/main/html/iframes.html)
## Formularios

Necesidad de una comunicacion entre la página web y servidores. 

```
<form>Contenido</form>
```
ATRIBUTOS DE FORMULARIOS:

- `id` Es importante que los formularios sean únicos.
- `action` A dónde se envían los datos.
- `method`
    * `"get"` (No usar, es necesario a veces)
    * `"post"` Vía cabecera

EJEMPLO
```
<form id="formulario1" action="recibeform.html" method="post"
        style="border: 1px #000 solid;margin: 30px;padding: 30px;background-color: #f2f2f2;">
    
        <h2>Nuestro formulario</h2>
    
        <fieldset>
            <legend>Aquí son tus datos de contacto:</legend>
    
            <div>
                <input id="formulario1_nombre" name="nombre" pattern="[A-Za-z0-9]+" required type="text" value="Pepe"
                    placeholder="Aquí tu nombre" />
                <p></p>
                <input type="password">
    
                <p></p>
                <textarea cols="40" name="objeto3" spellcheck="true">camion azul</textarea>
    
                <p> </p>
                Número entre 10 y 50, de 5 en 5. Valor por defecto: 25
                <p></p>
                <input type="number" name="numero" value="25" min="10" max="50" step="5" />
    
                <p></p>
                Su misma versión, utilizando el slider en un rango numérico
                <input type="range" name="numrango" value="25" min="10" max="50" step="5" />
    
                <p></p>
    
                Fecha <input type="date">
                <p></p>
                Hora <input type="time">
    
                <p></p>
                <input type="radio" name="sexo" value="H" /> Hombre
                <input type="radio" name="sexo" value="M" /> Mujer
                </p>
    
                Casillas de verificación (marcada por defecto)
                <input type="checkbox" name="empresa" checked />
                <p></p>
                Casillas de verificación (marcada por defecto)
                <input type="checkbox" name="empresa" checked />
                <p></p>
                Casillas de verificación (marcada por defecto)
                <input type="checkbox" name="empresa" checked />
                <p></p>
                Casillas de verificación (marcada por defecto)
                <input type="checkbox" name="empresa" checked />
                <p></p>
    
                <select name="combo">
                    <optgroup label="Opciones básicas">
                        <option value="1" label="Opcion 1"> </option>
                    </optgroup>
    
                    <optgroup label="Opciones avanzadas">
                        <option value="2" label="Opcion 2"> </option>
                        <option value="3" label="Opcion 3"> </option>
                    </optgroup>
                </select>
            </div>
    
            <p></p>
    
            <div>
                <input type="submit" value="Enviar formulario" />
            </div>
        </fieldset>
    
    
    
    </form>
```

- `fieldset` Grupo de campos.
- `legend` Legenda del fieldset.
- `action` Hay que enviar los datos del formulario a un servidor. 

### Atrubutos de los campos

Los campos de un formulario empiezan siempre como `<input type=" ">`

- `id`
- `name`
- `type` (ver tipos de campos)
- `value` Valor por defecto
- `placeholder` Indica que hay que escribir en ese campo
- `required` Para validar que el campo esté lleno en el lado cliente. Tiene sus problemas, hay que hacerlo en el servidor también. 
- `pattern` Para validar un patrón. Por ejemplo, solo números y letras. Tiene sus problemas, hay que hacerlo en el servidor también.

### Tipos de campos (`type`)

- BOTÓN. `type = "submit"`
- TEXTO. `type = "text"`
    * `type = "tel"` Teléfono. (Hay que especificar que tipo de teléfono)
    * `type = "url"` URL
    * `type = "email"` Email, con arroba
    * `type = "password"` Contraseña. Aparecerán     puntitos al escribir. 
    * `type = "textarea"` Mucho texto.
- NÚMEROS.
    * `type = "number"` Campos numéricos. Tiene como atributo `min`, `max` y `step`. 
    * `type = "range"` Slider. 
- FECHA Y HORA. 
    * `type = "date"` 
    * `type = "time"`
    * `type = "datetime-local"` 
- CASILLAS DE VERIFICACIÓN. 
    * `type = "radio"` Solo se marca una de ellas.
    * `type = "checkbox"` Todas las que queramos.
- LISTAS. 
    
```
<select name="combo">
    <optgroup label="Opciones básicas">
        <option value="1" label="Opcion 1"> </option>
    </optgroup>    
    <optgroup label="Opciones avanzadas">
        <option value="2" label="Opcion 2"> </option>
        <option value="3" label="Opcion 3"> </option>
    </optgroup>
</select>
```
    
- ARCHIVOS. 
    * `input type="file"`
    * Hay que poner en el formulario enctype="multipart/form-data
- OCULTO. `type = "hidden"` No se ve. Es muy utilizado. Envía información que no corresponde llenar al usuario. Datos necesarios como el número id de una campaña. 

### Seguridad
Cuidado con los datos recogidos. Siempre hay que pasarlos por una validación de servidor. Si no se hiciera así, el hacker puede cambiar el destino de los datos y utilizar el formulario para recoger los datos en un sitio que no le correspondía. 



## Tablas

Bastante en desuso porque es difícil para el responsive. Utilizar si necesitamos muchos datos ordenados. 

... 

[GitHub-Tablas](https://github.com/lierniortiz/Programazio-teoria/blob/main/html/tabla.html)

[GitHub-Tabla modelo](https://github.com/lierniortiz/Programazio-teoria/blob/main/html/tabla-modelo.html)

## Imágenes

Es un recurso, un `src`.

Cuidado con las licencias. En pixabay hay que ver que tengan licencia pixabay. No porque sea gratis significa que sea gratuita la licencia comercial. Además, hay que intentar utilizar el tamaño más pequeño posible. 

PIXLR es un buen editor de fotos. Es facil cambiar el tamaño de la foto al que queramos. `Imagen > Tamaño de imagen`. Luego tenemos en cuenta a cuanto lo hemos cambiado para meter esos datos en el elemento como se muestra a continuación. 

```
<img src="dog-gc4b1be3a9_1920.jpg"
        alt="Es una imagen de un perrito" width="400" height="453" />
```
 * `img` No tiene cierre. 
 * `src` Dónde está la imagen.
 * `alt` Lo que aparece si la imagen no se carga.
 * `width` y `height` Aunque luego cambiemos esto con CSS conviene meter estos datos. 

 TIPOS:

 * PNG
 * JPG
 * SVG
 * GIF. Intentar evitar
 * WEBP. Alternativa libre de Google al JPEG.

### Iconos
 [Librería de iconos google](https://fonts.google.com/icons)

 Si abrimos un icono y lo descargamos en SVG. Lo podemos abrir con chrome y `ver codigo fuente de la pagina`. De ahí podremos conseguir lo que hay que escribir en el HTML para ver ese icono. 

 Después podremos jugar con su estilo con `fill: red` por ejemplo.

### Responsive con `<picture>`

```
<picture>
    <source media="(min-width: 300px) and (max-width: 600px)" srcset="dog-gc4b1be3a9_1920.webp" />
    
    <img src="dog-gc4b1be3a9_1920.jpg" alt="HTML5 logo" />
</picture>
```

Si la pantalla es entre 300px y 600px se pondrá la primera imagen (la que esta en media), sino la segunda. 

## Video y audio

[GitHub-Audio](https://github.com/lierniortiz/Programazio-teoria/blob/main/html/audio.html)

[GitHub-Video](https://github.com/lierniortiz/Programazio-teoria/blob/main/html/video.html)

 
