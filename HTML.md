# HTML

- La web es un conjunto de documentos HTML enlazados a través de hipertexto , se ve a través del navegador
- HTML es un ***Lenguaje de marcado***
- *HTTP* es un protocolo para transferir o compartir documentos HTML

## 1. SINTAXIS

- **Atributo:** datos adicionales a una etiqueta : nombre= tipo atributo;

  ```html
  <h1 id= "main-title"> <!-- ETIQUETA APERTURA-->
      Curso HTML5 desde Cero (2017) <!-- CONTENIDO -->
  </h1> <!-- ETIQUETA CIERRE-->
  
  ```

- Etiquetas self closing o vacías **(meta): **

  ```html
  /* ESTRUCTURA BASICA*/
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Document</title>
  </head>
  <body>
      
  </body>
  </html>
  ```



## 2. ETIQUETAS ESENCIALES

- **Head** para metadata ,datos que el navegador no muestra como: lenguaje, CSS, JavaScript, título, idioma,descripción, etc.

- **Body** esta todo el contenido que el navegador muestra 

- **Atributo lang** es para el lenguaje que estas usando : es(español)

- **Etiqueta `<meta charset (atributo)>` para metadatos, UTF 8** garantizan que los caracteres aparezcan bien .

  ```html
  <meta charset="UTF-8">
  ```

  

- **Etiqueta title** para títulos

- `<link rel = shortcut icon>` **para poner el icono de la página en la barra del navegador**

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Título de mi página Web</title>
      <link rel = "stylesheet" href="styles.css">
      <link rel = "shortcut icon" href="favicon.png">
  </head>
  <body>
      <h1>Título de mi página Web</h1>
      <script src= "scripts.js"></script>
  </body>
  </html>
  ```
  - NOTA: *Los scripts siempre van al final del body*

- Tenemos los siguientes encabezados:

  ```html
  <h1>Encabezado 1</h1>
  <h2>Encabezado 2</h2>
  <h3>Encabezado 3</h3>
  <h4>Encabezado 4</h4>
  <h5>Encabezado 5</h5>
  <h6>Encabezado 6</h6>
  ```

- Otras etiquetas:
  - **Header** es un encabezado

  - **Nav** barra de navegación

  - **Article** elemento de contenido único

  - **Section** Secciones divisiones de la pagina

  - **Aside** etiqueta que no tiene que ver con la pág. como publicidad , etc

  - **Footer** poner notas al pie, créditos etc

    ```html
    <header></header>
    <nav></nav>
    <article>
        <h1>Titulo1</h1>
        <section>
            <h2>Subtitulo</h2>
        </section>
     </article>
     <aside></aside>
     <footer></footer>
    ```

    - Poniendo html:5 te autogenera el código en el editor de código
    - **Control+/ (slash) para comentar código**



## 3. ETIQUETAS DE CONTENIDO

### 3.1. Listas Anidadas

- **ul: another list (lista desordenada) –** el mejor ejemplo de ul es un menú de navegación

- **ol: other list (lista ordenada)**

- **li: list ítem**

  ```html
  <ul>
      <li>Item de lista 1</li>
      <li>Item de lista 2
          <ol>
              <li>Subitem de lista 1</li>
              <li>Subitem de lista 2</li>
          </ol>
      </li>
      <li>Item de la lista 3</li>
  </ul>
  ```

### 3.2. Listas de Definición: 

- Sirven par indicar un termino y una definición 

- Sus elementos son:

  - **dl : definition list**
  - **dt: definition term**: termino de definición
  - **dd: definition description**: descripción de la definición

  ```html
  <dl>
     <dt>Peru</dt>
     <dd>Lima</dd>
     <dt>Colombia</dt>
     <dd>Bogota</dd>
     <dt>Bolivia</dt>
     <dd>La paz</dd>
  </dl>
  ```

### 3.3. Figure y Caption

- **Etiqueta figure** sirve para poner un contenido relacionado pero que rompa el flujo del contenido (similar al aside) : una imagen relacionada, ejemplo Machu Picchu, imagen, video, código , etc

- **Etiqueta figcaption** es la leyenda o descripción del figure (opcional)

  ```html
  <figure>
      <pre>
      <code>
           function hola () {
               return "hola"
           }
       </code>
       </pre>
   <figcaption>
       Declaracion de una funcion de Javascript
   </figcaption>
  </figure>
  ```

### 3.4.  Otros elementos

- **Etiqueta main** es el mas importante porque aquí va todo el contenido importante, p es un párrafo

- **Etiqueta hr** es para romper la secuencia

- **Etiqueta pre** es pre formateado , el navegador tomará tal cual esté el contenido, respeta saltos de línea y espacios

- **Etiqueta blockquote** es para resaltar o destacar citas

  ```html
  <main>
      <p>Este es un parrafo, un elemento de bloque de texto</p>
      <hr>
      <pre>
      Este texto
      	se representara igual
      en el navegaodr
      </pre>
      <bloqueote> Use para destacar citas</bloqueote>
  </main>
  ```

### 3.5. Divisiones

- Alt+shift + fecha abajo para duplicar líneas

  ```html
  <div class="user">
      <div class= "user-name">
          <p> Greis Loyaga</p>
      </div>    
  </div>
  ```



## 4. ETIQUETAS Y LÍNEAS DE BLOQUE

### 4.1. Etiquetas Inline y de Bloque

- **Un elemento de bloque** visualmente reserva todo el espacio disponible en pantalla , y el siguiente elemento aparece debajo del otro párrafo : ejemplo un párrafo `<p>` es un elemento de bloque

- **Un elemento de línea** se ubica uno al lado del otro ejemplo: `<span>`

- **Un elemento de línea debe estar dentro de un elemento de bloque** , algunos ejemplos de elementos de línea son:

  - **Strong** es un texto mas importante

  - **Em** es para darle énfasis dentro del texto 

  - **Cite** para citar

  - **Dfn** es definition es para definir algo o explicar que significa una sigla

  - **Code** para poner fragmentos de código

  - **Data** para poner datos que vengan de algún programa, o datos de una estadística, etc 

  - **br** para saltos de línea 

  - **q** es para citas 

  - **abbr** de abreviación

  - **del** para indicar que un texto ha sido eliminado

  - **wbr** Ruptura de palabras , se pone en el medio de la palabra si es muy grande

  - **span** no significa nada , pero es un contenedor de texto , similar a div

  - **sup** superíndice

  - **sub** subíndice

  - **time** para poner hora o fechas

  - **mark** destacar algunos elementos (resaltador)

  - `<a href =”"> </a>` enlaces

    ```HTML
    //ELEMENTOS DE TEXTO COMUNES
    <p>
        <small></small>
        <strong></strong>
        <em></em>
        <cite></cite>
        <dfn></dfn>
        <code></code>
        <data></data>
     //ELEMENTOS DE TEXTO COMUNES
        <br>
        <q></q>
        <abbr></abbr>
        <del></del>
        <wbr>
        <span></span>
        <i></i>
        <b></b>
        <u></u>
     //ELEMENTOS DE TEXTO COMUNES
        <sup></sup>
        <sub></sub>
        <time></time>
        <mark></mark>
        <a href=""></a>
    </p>
    ```



### 4.2.  Enlaces

- Un enlace es un trozo de texto o imagen, es un hipertexto, haces click y te lleva a otra parte, con el atributo `href` define a donde va.

- Tenemos rutas absolutas y relativas.

  

  ```html
  <h1>Enlaces</h1>
  <p>
      <!-- RUTAS ABSOLUTAS NO SE VAN A REPETIR EMPIEZA CON EL PROTOCOLO HTTPS -->
      <a href="https://ed.team">Educacion con Honestidad</a>
      <!-- RUTA RELATIVA MISMA CARPETA  destino.html = ./destino.html -->
      <a href="usuarios.html">Usuarios</a>
      <a href="./usuarios.html">Usuarios</a>
      <!-- RUTA RELATIVA, CARPETA SUPERIOR-->
      <a href="../usuarios.html">Usuarios</a>
      <!-- RUTA RELATIVA, DOS CARPETAS ARRIBA Y SUBCARPETA-->
      <a href="../../usuarios/usuarios.html">Usuarios</a>
      <!-- RUTA RELATIVA A LA RAIZ-->
      <a href="/usuarios.html">Subcarpeta</a>
  </p>
  ```



### 4.3. Marcadores

El destino es un # con un texto, ese texto debe coincidir con un `id` de la misma página

```html
<!-- CADA href debe coincidir con el id, al presionar el enlace te lleva al id indicado -->

<h1>Marcadores</h1>
<ul id="indice">
    <li><a href="#capitulo1">Capitulo1</a></li>
    <li><a href="#capitulo2">Capitulo2</a></li>
</ul>

<h2 id="capitulo1">capitulo1</h2>
<p><a href="#top">Ir al indice</a></p>
<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Similique expedita eum quas et nihil illum repellendus qui minus inventore dolor ab hic quasi cupiditate vero quibusdam, pariatur dolorum cum in.
</p>

<h2 id="capitulo2">capitulo2</h2>
<!-- #TOP HACE QUE EL ENLACE VAYA AL INICIO DE LA PAGINA -->
<p><a href="#top">Ir al indice</a></p>
<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Similique expedita eum quas et nihil illum repellendus qui minus inventore dolor ab hic quasi cupiditate vero quibusdam, pariatur dolorum cum in.
</p>
```

## 5. IMÁGENES

### 5.1. Imágenes

- **Bitmap**
- **Vector** perfectos para logotipos (svg)
- **JPG** para foto y **PNG** Para iconos con transparencia o gráficos con texto con color plano
- **WEBP** reemplaza a jpg y png pero solo sirve para Chrome

### 5.2.  Viewport y Device Pixel Ratio

- Computadora siempre tiene 1 de device pixel ratio
- Dependiendo del viewport vemos el device pixel ratio de los dispositivos ejemplo:
- Galaxy S5 (360X640) TIENE un device pixel ratio de 3.
- Ratio es razón que significa división, división píxeles reales **(el del manual del celular)/(tamaño de la pantalla del celular)=Device Pixel Ratio**
  - Ejemplo: 1920px reales del celular / 640 px tamaño de la pantalla del celular =3 es decir, que para que una imagen se vea bien en el celular iPhone, la imagen que pongas debe ser 3 veces el tamaño de la pantalla.

- Tenemos que tener imágenes tanto para la computadora o móviles con diferente pixel ratio

### 5.3.  Atributo SRCET

**SRCSET** es un conjunto de imágenes con una ruta para diferentes pixel ratio o viewport.

```html
<img src="img/novia.jpg" alt="" srcset="img/man.jpg 1.5x, img/dog.jpg 2x">
```

- Etiqueta `<picture>`

```html
<picture>
    <!-- LA ETIQUETA PICTURE ES COMO UN IF SI SE CUMPLE LA PRIMERA CONDICION LO MUESTRA, SI NO 
    LEE LA OTRA , DE LO CONTRARIO MUESTRA A LA IMAGEN POR DEFECTO SI NO CUMPLE NINGUNA -->
    <source srcset="img/dog.jpg" media="(min-width:800px)">
    <source srcset="img/man.jpg" media="(min-width:500px)">
    <!--VALOR POR DEFECTO  -->
    <img src="img/novia.jpg" alt="Foto novia">
</picture>
```



## 6.  MICRODATOS Y OPENGRAPH

- Microdatos son atributos que se dan al contenido para decir que cada cosa es un elemento. 

- **SCHEMA** Para Google.

-  **OPENGRAPH** sirve para Facebook.

  

## 7. TABLAS

### 7.1. TABLAS

- Se usa para mostrar datos de manera tabular, ejemplo un reporte de estudiantes
- `<table> </table>` para hacer una tabla
- `<tr> </tr>` **table row** son las filas
- `<td> </td>` **table data** son las celdas, lugar donde pones los datos.
- Cuando usamos cabeceras o encabezados se necesita colocar antes el `<thead> </thead>`el dentro van los `<tr> </tr>` y `<th> </th>`
- Cabeceras: para hacerlo cabecera ponemos `<th> </th>`  que es **table header** o encabezado de tabla. Y para un `<thead> </thead>` se usa un `<tbody> </tbody>` donde ira todo el cuerpo y las filas.  
- Para las conclusiones de la tabla se usa un `<tfood> </tfood>` .

### 7.2. AGRUPAR CELDAS

- Atributo `colspan` indica cuantas columnas ocupa la celda 
- El atributo `rowspan` permite agrupar en las filas que ocupa una celda 
- La etiqueta `<caption> </caption>` es para darle titulo a la tabla 

```html
<!-- ELEMENTO TABLE -->
<table>
	<!-- SIRVE PARA AGRUPAR LAS COLUMNAS -->
    <colgroup>
        <col>
        <col>
        <col>
        <col>
        <col style="background: yellow;">
    </colgroup>
    <!-- CAPTION LE DA NOMBRE A LA TABLA -->
    <caption>Mi horario de clases</caption>
    <!-- SI USAS UN ENCABEZADO SE USA EL ELEMENTO THEAD -->
    <thead>
        <!-- TR SON LAS FILAS -->
        <tr>
            <!-- TH ES UN ENCABEZADO -->
            <th>Lunes</th>
            <th>Martes</th>
            <th>Miercoles</th>
            <th>Jueves</th>
            <th>Viernes</th>
        </tr>
    </thead>

    <!-- SE PONE TODO EL CUERPO EN TBODY-->
    <tbody>
        <tr>
            <!-- TD SON LAS CELDAS -->
            <td rowspan="2">PYTHON</td>
            <td>CSS</td>
            <td rowspan="2">JAVA</td>
            <td>C++</td>
            <td rowspan="2">MYSQL</td>
        </tr>
        <tr>
            <!-- TD SON LAS CELDAS -->
            <td>GO</td>
            <td>BIGDATA</td>
        </tr>
        <tr>
            <!-- colspan sirve para agrupar columnas -->
            <td colspan="5">recreo</td>
        </tr>
        <tr>
            <!-- TD SON LAS CELDAS -->
            <td>JAVA</td>
            <td>ALGORITMOS</td>
            <td>ANGUAR</td>
            <td>C</td>
            <td>SQL</td>
        </tr>
        <tfoot>
            <tr>
                <td>2 creditos</td>
                <td>4 creditos</td>
                <td>6 creditos</td>
                <td>5 creditos</td>
                <td>4 creditos</td>
            </tr>
        </tfoot>
    </tbody> 
</table>
```



## 8. FORMULARIOS

- **La etiqueta ** <`form> </form>` tiene un atributo action e indica que archivo va procesar este formulario. Estos formularios tienes campos: input(donde el usuario escribe datos)

- Para realizar un formularios colocamos la etiqueta: **<`form> </form>`**, dentro de la etiqueta `form` ponemos los diferentes inputs.

- **Nota:** en cada input debe haber un `name` para indicar que tipo de campo es y  poder mandarlo a la base de datos.

- Tipo de inputs:

  - **Tipo text** `<input> = <input type="text">`

    ```html
    <div>
        <!-- El elemento label le da un titulo a un campo -->
        <label>
            <!-- Input de tipo texto -->
            Ingrese su nombre:
            <!-- Todos los campos deben tener el atributo name que es el identificador 			unico de esos campos -->
            <input id="username" name="username">
        </label>
    </div>
    ```

  - **Tipo password**

    ```html
    <div>
        <label>
            Ingrese su contraseña:
            <input type="password" name="password" required>
        </label>
    </div>
    ```

  - **Tipo submit**

    ```html
    <!-- <button>Enviar</button> -->
    <!-- Input de tipo submit para enviar datos -->
    <input type="submit" value="Iniciar sesion">
    ```

  - **Tipo email**

    ```html
    <div>
        <label>
            Ingrese su correo:
            <input type="email" name="correo">
        </label>
    </div>
    ```

  - **Tipo date**

    ```html
    <div>
        <label>
            Ingrese su fecha de nacimiento:
            <input type="date" name="fecha">
        </label>
    </div>
    ```

- Atributo `placeholder`

  Cuando no se tiene un titulo de un campo se puede usar un placeholder.

  ```html
  <div> 
  	<input type="email" name="correo" placeholder="Ingrese su correo">
  </div>
  ```

- Etiqueta `<fieldset > </fieldset>` permite meter varios campos en una especie de contenedor.

  - Con una etiqueta `<legend></legend>` le da el nombre al fieldset(contenedor)

  ```html
  <fieldset>
      <legend>Tus datos personales</legend>
      <div>
          <!-- El elemento label le da un titulo a un campo -->
          <label>
              <!-- Input de tipo texto -->
              Ingrese su nombre:
              <input id="username" name="username">
          </label>
      </div>
      <div>
          <label>
              Ingrese su correo:
              <!-- Input de tipo email-->
              <input type="email" name="correo">
          </label>
      </div>
  </fieldset>
  ```

- Otros inputs:

  - **Input checkbox**

    Sirve para marcar opciones múltiples.

    ```html
    <fieldset>
       <legend>Tus pasatiempos</legend>
       <label><input type="checkbox">Musica</label>
       <label><input type="checkbox">Cine</label>
       <label><input type="checkbox">Deporte</label>
    </fieldset>
    ```

  - **Input radio**

    Sirve para escoger una sola opción.

    ```html
     <fieldset>
       <legend>Tu genero</legend>
       <label><input type="radio" name="genero">Hombre</label>
       <label><input type="radio" name="genero">Mujer</label>
       <label><input type="radio" name="genero">Prefiero no decirlo</label>
    </fieldset>
    ```

  - **Etiqueta select y option**

    ```html
    <fieldset>
       <legend>Select y opciones</legend>
       <label>Escoge tu pais</label>
       <!-- Select es una lista de opciones -->
       <select name="country" id="country">
           <!-- OPTGROUP PARA AGRUPAR ELEMENTOS -->
           <optgroup label="America Latina">
               <!-- Cada opcion es un elemento option -->
               <option value="pe">Peru</option>
               <option value="co">Colombia</option>
               <option value="ve">Venezuela</option>
            </optgroup>
    
           <optgroup label="Europa">
               <!-- Cada opcion es un elemento option -->
               <option value="es">Espana</option>
               <option value="it">Italia</option>
            </optgroup>
        </select>
    </fieldset>
    ```

  - **Etiqueta textarea**

    Sirve para escribir mensaje largos en un cuadro.

    ```html
    <textarea name="mensaje" cols="30" rows="10" 
    placeholder="Escribe tu mensaje"></textarea>
    ```

  - **Atributo `required`** (Campo obligatorio)

    ```html
    <input type="password" name="password" required>
    ```

  - **Atributo `readonly`** (El usuario solo puede ver el campo)

    ```html
    <input type="number" value="2" readonly>
    ```

## 9. MULTIMEDIA

```html
<video id="video" src="media/video.mp4" controls poster="poster.jpg"></video>
<audio id="audio" src="media/audio.mp3" controls></audio>
```



## 10. CONTENIDO INTERACTIVO

### 10.1. Contenido interactivo en HTML

- La etiqueta `<details> </details>` significa detalles y crea un acordeón(un titulo que se expande o cierra )

- La etiqueta `<dialog> </dialog>` es un modal , es como una pequeña ventana del documento que esta oculto y luego se muestra. Con el atributo `open` se muestra el modal

  ```html
  <!-- DIALOG ES UN MODAL: del mismo documento que esta oculto y luego se muestra -->
  <!-- Con el atributo open puedes mostrar el modal -->
  <dialog id="modal">
      <h2>Curso html5 desce cero</h2>
      <p>Precio:134</p>
      <p>Profesor Alvaro</p>
      <button id="close">Cerrar modal</button>
  </dialog >
  <button id="button">Abrir modal</button>
  <h1>Contenido interactivo</h1>
  
  <!-- DETAILS significa detalles y crea un acordeon : un titulo(widget)' que se expande o se cierra -->
  <details>
      <!-- SUMMARY SERIA COMO UN TITULO -->
      <summary>HTML</summary>
      <p>Lenguaje de marcado e hipertexto</p>
      <p>Se creo en 1990</p>
  </details>
  ```

### 10.2. Contenido embebido

- Cuando traes contenido de otro lugar a tu página web

- Se usa la etiqueta `<iframe> </iframe>`. Permite traer un página web con toda la estructura del documento.

  ```html
  <h1>Contenido Embebido</h1>
  <iframe width="560" height="315" src="https://www.youtube.com/embed/ErLP1daUjB8" 
  frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope;
  picture-in-picture" allowfullscreen></iframe>
  ```

  