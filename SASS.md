# **SASS**

## **1. Sintaxis**

### **1.1. ¿Qué es Sass?**

- Preprocesador escrito en Ruby en 2006
- Ventajas
  - Usado por proyectos líderes
  - Gran comunidad y soporte
  - Sintaxis sólida y similar a css
  - Se puede usar en cualquier entorno(no solo en Ruby) con libsass
- Sintaxis de Sass
  - Sintaxis Sass ( no recomendada , en desuso)
    - Basada en Haml
  - Sintaxis Scss (recomendada)
    -  Superset de css
    - Todo Css válido es válido en Sass
- Comentarios
  - `//Comentarios invisibles en la compilación`
  - `/*Comentarios visibles en la compilacion*/`

### 1.2. Compilar Sass

- Probar Sass desde el navegador
  - Sassmeiter
  - Codepen
- Usar compilador gráfico
  - Prepos (recomendada)
  - Codekit (Para Mac)
  - Koala
  - Scout
- Compilar por línea de comandos
  - Instalamos node js
  - Luego le damos `npm install -g node-sass` para poder compilar sass
  - Compilar archivos scss a css : `node-sass --watch directorio_sass --ouput directorio_css`
- Otras herramientas para compilar
- Css to Sass

### 1.3. Variables

- Las variables se declaran `$variable: valor` 

  - Las variables en Sass las utilizamos para almacenar información (valores) que vamos a usar más adelante.

  ```scss
  $size: 200px;
  ```

- default permite sobrescribir la variable antes y después

  ```scss
  $primary-color: blue !default;
  ```
  
- Interpolación de variables : `#{$nombre_variable}`

  - La interpolación nos permite colocar dentro de una variable el nombre de un selector y/o atributo.
  
    Para interpolar una variable usamos: `#{$var}`
  
  ```scss
  $size: 200px;
  p {
      $size : 20px;
      margin: $width;
      padding-top: $size;
    //interpolacion de variables
      width: calc(100% - #{$size});
  }
  ```
  
  

### 1.4. Anidamiento

- Es poder meter selectores dentro de otro

  ```scss
  ul {
      margin: 0;
      display: block;
      animation: menu 1s;
  
      @media screen and (min-width: 640px) {
          display: flex;
      }
  
      @keyframes menu {
          to {
              color: $color;
          }
      }
  }
  ```

- `&` para repetir el selector

  ```scss
  ul {
      margin: 0;
      display: block;
      animation: menu 1s;
  
      &:hover {
          color: green;
      }
  
      &::before {
          content: "Greis";
      }
      
      @media screen and (min-width: 640px) {
          display: flex;
      }
  
      @keyframes menu {
          to {
              color: $color;
          }
      }
  }
  ```

- Construir clases

  ```scss
  .menu {
      display: block;
  
      &-item {
          color: red;
      }
  }
  ```

  

### 1.5. Tipo de datos

- Strings

  - quote(hola) : pone comillas

  - unquote("hola") : le quita comillas

    ```scss
    $nombre: unquote($string: "Greis");
    body {
        content: "#{$nombre}";
        display: block;
    }
    //EN CSS
    //body {
      //content: "Greis";
      //display: block; } 
    
    ```

- Números

- Colores

  ```scss
  // $var : red;
  $var: darken(red,20);
  body {
      background: type-of($value: var);
      color: $var;
  }
  ```
  
- Booleans

- Maps

  - Los mapas contienen pares de key(claves) y valores, y facilitan la búsqueda de un valor por su key  correspondiente. Están escritos `(<clave>: <valor>, <clave2>: <valor2>)`. Los mapas deben escribirse entre paréntesis. 

    ```scss
  //MAPA
    $var: (
        color: red, //color: key , red : valor
        font: arial,
        size:20px
    );
    
    body {
        background: type-of($value: var);
        color: map-get($var , color);
    }
    ```
  
- Lists

  ```scss
  $var: 1px solid red //LISTA
  ```

### 1.6. @import

- `@import "archivo_scss";  @import "menu";`

- Para ignorar un archivo scss  `_archivo.scss`

  ```scss
  @import"config";
  @import "menu";
  
  body {
      background: red;
  }
  ```

## 2. Ciclos y Condicionales 

### 2.1 @ extend

- Permite crear placeholder e importarlos o extenderlos en selectores

- `%` : este es un placeholder , sirve para guardar bloques de estilo que luego se van a reutilizar

- ```scss
  // @extend
  %button {
      display: inline-block;
      margin: 1em 0;
      padding: .5em 1.5em;
  }
  
  .button {
      @extend %button;
  }
  
  .button-alert {
      @extend %button;
      background: red;
      color: #fff;
  }
  
  .button:hover {
      transform: translateY(-5px);
  }
  
  .button:active {
      @extend .button:hover;
  }
  ```

  

### 2.2. Condicionales

- `@ if $condicion`

  ```scss
  @if 5 < 3 {
      * {
          outline: 1px solid red;
      }
  } @else if 3 < 5 and 1 == 1  {
      * {
          display: block;
      }
  } @else {
      * {
          color: green;
      }
  }
  ```

### 2.3. Ciclo For

```scss
@for $i from 1 through 100 {
    @if $i % 2 ==0{
    .column-#{$i *5} {
        width: $i * 5%;
    }
}
}
```

### 2.4. Ciclo Each

- `@each $vriable in list o map` : itera sobre una lista o sobre un map

```scss
//CICLO EACH
//lista
$colors: red green blue ;

@each $color in $colors {
    .button-#{$color} {
        background: $color;
    }
}

//Iterar sobre mapas

$colors: (
    primary: red,
    secondary: green,
    terciary: blue
);

$brakpoints: (
    small: 360px,
    medium: 640px,
    large: 1024px
);

@each $key, $value in $colors {
    .button-#{$key} {
        background: $value;
    }
}

```

## 3. Mixins

- Son bloques de código reutilizables que pueden contener selectores, reglas css y lógica interna
- Los mixins son obviamente necesarios cuando necesitas configurar los estilos usando argumentos
- `@mixin nombre` , `@include nombre-mixin`(incluimos el mixin para llamarlo en el styles.scss)
- Directiva `@content`

## 4.  Funciones

- Las funciones se definen usando  

  ```scss
  @function <name>(<arguments...>) { 
  ... 
  @return $var
  }
  ```


### 4.1. Funciones de string

- `quote($string)` : pone comillas
- `unquote($string)` : le quita comillas
- `str-index($string , "letra_a_buscar")` : devuelve el índice del caracter ingresado

- `str-length($string)`

- `str-index($string)`

- `to-upper-case `

- `to-lower-case`

  ```scss
  $width: 1px;
  $style: solid;
  $color: red;
  
  body {
      border: unquote ($width+ " " + $style + " " + $color);
      &::before {
          content: quote($style);
      }
      index: str-index($style, "s")
      index: str-length($style) //devuelve el tamaño de string
  
  }
  ```

### **4.2. Funciones de numero**

- `percentage($number)`

- `max($number)`

- `min($number)`

- `floor($number)` : redondea hacia abajo

- `ceil()` : redondea hacia arriba

- `round` : redondea al mas cercano

- `random()`

  ```scss
  //FUNCIONES PARA NUMEROS
  @function columns ($column, $total-columns) {
     @return percentage($column / $total-columns);
  }
  @for $i from 1 through 12 {
          .cols-#{$i}{
              width:columns($i, 12)
          }
  }
  
  body {
      width: floor(34.5);
      width: ceil($number: 35.6);
      width: round(23.7);
      width: random();
  }
  ```

### 4.3.  Funciones de listas y mapas

- **LISTAS**

  - `nth($list , n)` : encontrar un elemento, donde "n" es la posición del elemento

    ```scss
    $var: 1px solid red;
    body {
        background: type-of($value: var);
        color: nth($var, 3 );
    }
    //EN CSS
    //body {
     // background: string;
     // color: red; }
    ```

    

  - `index ($list, $value)` : obtener el índice de un elemento

    ```scss
    $var: 1px solid red
        body {
        background: type-of($value: var);
        border-color : index($var , red) // devueleve el indce 3
        color: $var;
    }
    ```

    

  - `join ($list1, $list2, $lis3 , separdor : space | comma)`: juntar listas, y pasar el separador 

  - `append($list, $value, $separador: space | comma)` : agregar un valor al final de la lista

    ```scss
    $border: 1px solid red;
    $border2 : 1px dotted green;
    body {
        border: nth($border, 3 );
        border: index($border , solid);
        border-color: join($border, $border2 ,comma);
        border: append(1px solid , $color);
    // }
    ```
    
    

- **MAPAS**

  - Buscar un valor: `map-get($map, $key)` Esta función devuelve el valor en el mapa asociado con el key dado. Regresa null si el mapa no contiene la clave.

    ```scss
    $var: (
        color: red, //color: key , red : valor
        font: arial,
        size:20px
    );
    
    body {
        background: type-of($value: var);
        color: map-get($var , color);
    }
    ```

  - `map-keys($map)` : permite obtener todas las claves(keys) en el mapa

  - `map-values($map)`

  - `map-has-key($map,$key)` : Devuelve un boolean. Si `$map`contiene un valor asociado con `$key`.

    ```scss
  $colors : (
         primary: green,
         secondary: red,
         terciary: yellow
     );
    
     @function color ($color-key) {
         @if map-has-key($colors, $color-key ) {
             @return map-get($colors , $color-key )
         }
     }
    
     body {     
         border-color: color(primary);
     }
    
    ```
  
    
  
  - Agregar a un mapa :`map-merge($map1,$map2)` devuelve un nuevo mapa que contiene todos los pares clave / valor en ambos  argumentos.
  
    ```scss
  $var: (
        color: red,
        font: arial,
        size: 20px
    );
    
    $light-weights: ("lightest": 100, "light": 300);
    $heavy-weights: ("medium": 500, "bold": 700);
    
    $var: map-merge($light-weights, $heavy-weights);
    
    body {
        background: type-of($value: var);
        font-size: map-get($var , bold);
    }
    
    //EN CSS
    //body {
    //background: string;
    //font-size: 700; }
    ```
  
    

### **4.4. Funciones de Introspección**

- `inspect()` permite devolver el valor dentro del parámetro, es como un console.log en js

- `type-of()` devuelve el tipo de dato

- `unit()` devuelve la unidad de un numero como string

- `unitless()` devuelve un boolean. Devuelve true si el numero no tiene unidad

  ```scss
  $color: green;
  $color: (
      primary: yellow,
      secondary: red
  );
  
  body{
      // color: inspect($color);
      color: unit(10px);
      color: unitless(10);
  }
  ```

- `mixin-exists($mixin)` si existe el mixin, true o false

  ```scss
  @mixin button {
      color: red;
  }
  
  @if mixin-exists(button) {
      body {
          background: green;
      }
  }
  ```

- `function-exists(function)`:true o false

- `variable-exist($variable)`: true o false

- `global-vriable-exists($variable)`



## 5. Colores

- **RGB (red, green blue)**

  - 256,256,256 == 2^8, 2^8, 2^8 = 16M colores= profundidad

- **NOTACION HEXADECIMAL**

  - #RRGGBB

- **HSL** 

  - hue , saturation, lighten
    - hue: tono de color( de 0 a 360 grados)
      - 0/360 : red
      - 60: yellow
      - 120: green
      - 180: cyan
      - 240: blue
      - 300: magenta
    - saturation: intensidad del color , de gris al color puro , 100% el color puro
    - lighten: cantidad de luz (0% da negro , 100% blanco, el color puro esta en 50%)

- **FUNCIONES SASS**

  - **RGB**

    Para obtener los valores de cada canal

    - red($color)
    - green($color)
    - blue($color)

  - **HSL**

    - hue($color)

    - saturation($color)

    - lightness($color)

      ```scss
      body {
          $color: rgb(14,28,94);
          h: hue($color);
          s: saturation($color);
          l: lightness($color);
      }
      ```

      - darken($color, cantidad) /canal de luz
      - lighten($color, cantidad) /canal de luz
      - saturate($color, cantidad) / canal de saturation
      - desaturate($color, cantidad) /canal de saturation
      - adjust-hue($color, cantidad)

## 6. Debugging

- **Opciones de compilacion**
  - Comando : `node-sass scss -o css --output -style = "valor"`
  - `node-sass scss -o css --output-style=expanded --source-comments`
  -  Tenemos los siguientes valores `--output-style=expanded|compressed|compact`
    - compressed: en una sola linea
  - `--output-style = 'valor' --source-comments` : nos genera comentarios con la linea original que lo genero en scss
- **Sourcemaps**
  - `$ node-sass scss -o css --source-map=true`                             

## 7. Estructura de proyecto

- **SMACSS** : organizar en carpetas de la siguiente manera
  - base(etiquetas HTML)
  - módulos(componentes reutilizables : menú, tarjetas, acordeones , bloque reutilizable)
  - layout(geometría y posición )
  - theme(tipografía y color , identidad visual de la marca)
  - estado (elementos que cambian)
- **ITCSS**
- **7in1**
