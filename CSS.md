# **CSS**

## **1. Introducción**

Css(cascade style sheets) es un lenguaje de estilos. Se encarga de escribir el renderizado de documentos estructurados como HTML Y XML( SVG)

### 1.1. Conectar html con css

- `<link rel="stylesheet" href="styles.css">`

### **1.2. Sintaxis**

- Comentario : `(CONTROL + /)`

  - /\* ESTE CODIGO ES TEMPORAL\*/

- **Regla CSS tiene:** 

  - Selector : Indica a que elemento html se le aplicara los estilos

  -  Bloque: o bloque de declaración que esta entre llaves, cada linea es una declaración, cada declaración tiene una propiedad y su valor


###  **1.3. Variables**

Una variable es un lugar donde almacenas un valor par poder reutilizarlo

<img src="https://res.cloudinary.com/practicaldev/image/fetch/s--gKvVfErM--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/904ahjro7e3yezzl1m42.png" alt="CSS Variables - DEV" style="zoom: 50%;" />



## **2. SELECTORES**

**2.1. Tipo Sencillo**

- **Selector de etiqueta** : Selector de elemento o de tipo , donde el selector es solo es una etiqueta HTML/XML

  ```css
  h1 {
      background: red;
      color: white;
  }
  ```
  
- **Selector de clases** : Las clases nunca empiezan con numero

  ```css
  .title {
      background: red;
      color: white;
  }
  ```
  
- **Selector ID** : Identificador único que no se va repetir nunca, Los selectores de id se indica con un hash**(#)**

  **NOTA:** se recomienda su uso para JavaScript, es un mala practica ya que no se puede reutilizar.

  ```css
  #title {
      background: red;
      color: white;
  }
  #parrafo {
      background: seagreen;
      color: white;
  }
  ```
  
- **Selector Universal** :Selecciona todos los elementos

  ```css
  * {
      color: brown;
  }
  ```
  
- **Case Sensitive** : 

  - Los selectores CSS son case insensitive no importa mayúsculas y minúscula. 

  - HTML Y XML (TAGS-etiquetas ) son insensitive (no diferencia mayúscula de minúscula)

  - HTML Y XML (Atributos) son case sensitive (diferencia mayúscula de minúscula)

    ```css
    /* LOS TAGS (ETIQUETAS) PUEDEN IR EN MINUSCULA O MAYUSCULA */
    P {
        color: green;
    }
    /* ATRIBUTOS DEBEN SER EN MINUSCULA IGUAL A COMO SE ECRIBIO EN EL BODY */
    .parrafo {
        background: yellow;
    }
    ```

### **2.2. Tipo Compuesto**

- Cuando hay mas de un selector. Tenemos:

  - **Agrupados:**  

    - `.a, .b` 

    - Agrupar selectores con coma, a todos ellos se les aplica el mismo estilo. 

    - Es recomendable poner cada selector en diferente línea de código.

      ```css
      .title, 
      .parrafo {
          color: hotpink;
      }
      ```

  - **Descendientes**: 

    - Indica cuando un elemento es hijo, nieto o cualquier descendiente

    - `.a .b`el espacio en blanco indica que `.b` es descendiente de `.a`

    - Cualquier elemento que este dentro de otro.

    - **NOTA** : Cuidado con los espacios en blanco `.a.b!= .a .b`

      ```css
      body {
          font-size: 2em;
      }
      .list .tag {
          color: red;
      }
      ```

  - **Hijo Directo:** 

    - `a > b`  donde b es hijo directo de a

      ```css
      /* SELECTOR HIJO DIRECTO  */
      body {
          font-size: 2em;
      }
      li > ul {
          display: none;
      }
      li:hover ul {
          display: block;
      }
      ```

  - **Hermano siguiente:** selecciona el elemento que esta justo después de otro elemento : `a + b`

    ```css
    :root {
        --title: purple;
        --subtitle: blue;
    }
    .title1 {
        color: var(--title)
    }
    .title2 {
        color: var(--subtitle)
    }
    .subtitle {
        font-size: .5em;
        margin: 0;
    }
    .title1 + .subtitle {
        color: var(--title)
    }
    .title2 + .subtitle {
        color: var(--subtitle);
    }
    ```

  - **Hermanos siguientes:**  `a~b`

    ```css
    <body>
       	<input type="checkbox" class="check">
        <p class="enabled">Activado</p>
        <p class="disabled">Desactivado</p>
    </body>
    .enabled {
        display: none;
    }
    .check:checked ~ .enabled {
        display: block;
    }
    .check:checked ~ .disabled {
        display: none;
    }
    ```

### **2.3. Tipo Atributo**

- Se encierran entre [] . Tenemos:

  - **Sencillos:**

    - **Atributo y valor** : `[attr= “value”]`

    -  **Solo atributo:** `[attr]`

      ```css
      [type="email"] {
          border: 1px solid blue;
      }
      [required] {
          border: 2px solid red;
          margin: .5em;
      }
      ```

  - **Con Comodines:**

    - **Empieza con**: `[attr^= “value”]`

      ```css
      [href^="/"],
      [href^="https://ed.team"]
       {
          color: red;
          background: none; 
      }
      ```

    - **Termina con** : `[attr$= “value”]`

      ```css
      [href$="pdf"] {
          color: red;
          background: url(img/pdf.png) no-repeat center right / 2rem;
      }
      ```
  
- **Contiene:** `[attr\*= “value”]`
  
  ```css
      [class*="button-"] {
          display: inline block;
          margin: 1em;
      }
      .button-cta {
          background: orange;
      }
      .button-alert {
          background: red;
      }
  ```
  
  ​    

## **3. ESPECIFICIDAD , HERENCIA Y CASCADA**

### **3.1. Introducción**

- Arquitectura: es la forma que organizamos los archivos css en un proyecto como organizamos los componentes, tipografía, botones. Etc.
-  METODOLOGIA PARA CSS: SMACSS, OOCSS, ITCSS
- Cuando traes librerías o frameworks puede generar conflictos

### **3.2. Especificidad**

**Que estilo regla es la mas especifica, es a nivel de selectores.**

- Las etiquetas valen 1
- Las clases valen 10
- Los id valen 100
- Los estilos inline valen 1000
- Los !important = el poderoso bill (malo) 

### **3.3. Cascada**

Lo que viene después sobrescribe a lo que está antes. Tomando en cuenta que ambos selectores tienen la misma especificidad.

### **3.4. Herencia**

Los descendientes heredan algunas propiedades de sus padres

- **INITIAL** Resetear un elemento a su valor inicial

- **INHERIT** Obliga a que un elemento herede una propiedad

  ```css
  ul{
      color: red;
  }
  li{
      color: initial;
  }
  ul span {
      color: inherit;
      font-size: inherit;
  }
  ```

  

## **4. BOX MODEL**

El Box Model es el algoritmo a través del cual el navegador dibuja las cajas en la pantalla. Para hablar del box model debemos tener presente alguno conceptos base:

### **4.1. Layout**

- Es la geometría de los elementos que define como, con que tamaño, con que separación respectos a los elementos adyacentes y en que posición se van a dibujar en la pantalla
- Es la geometría de cada elemento , cuanto mide cada elemento(largo, ancho), donde va a dibujarse.
-  **Propiedad width(ancho) y height(alto)** es para definir el ancho y alto de un elemento

### **4.2. Elementos Inline y de Bloque**

- **INLINE: en css inline( display: inline)**
  - No crean nuevas líneas para cada elemento
  - Tienen ancho pero no se puede definir un alto
  - Se ajustan al contenido

- **DE BLOQUE (display: block)**
  - Crea una nueva línea para cada elemento
  - Ocupan todo el espacio horizontal disponible
  - Tienen ancho y alto

- En CSS tenemos un tercer tipo de elemento que es el **inline-block** que combina lo mejor de ambos :
  - Tienen un alto y ancho que puede ser modificado.
  - No crean nuevas líneas para los elementos.

- El **DISPLAY NONE** oculta un elemento

### 4.3. Box Model

- El Box Model es el algoritmo a través del cual el navegador dibuja las cajas en la pantalla

- El box model solo se aplica a los elementos de bloque. Tenemos 3 tipos de caja

  #### **4.3.1. Caja de Contenido(CONTENT BOX)**

  La definimos con las propiedades **width (ancho) y height (alto)**

  #### **4.3.2. Caja de Padding (PADDING BOX)**

  La definimos con la propiedad **padding.** Es la separación del contenido y el limite de la caja (BORDER)

  #### **4.3.3. Caja del Border (BORDER BOX)**

  La definimos con la propiedad **border**

  #### **4.3.4. Margin**

   Una ultima caja que es invisible alrededor

  ```css
  box {
      background: yellow;
      background-clip: content-box;
      /* BOX  MODEL */
      /* CONTENT BOX  CAJA INTERNA*/ 
      width: 500px;
      height: 300px;
      /* PADDING BOX CAJA INTERNA */
      padding: 50px;
      /* BORDER BOX CAJA INTERNA*/
      border: 30px solid black;
      /* MARGIN CAJA INVISIBLE EXTERNA*/
      margin: 100px;
      /* BOX SIZING COMO EL NAVEGADOR CALCULARA EL TAMAÑO DE LA CAJA */
      box-sizing: border-box; 
  }
  ```

  ![Diagrama del modelo de cajas](https://mdn.mozillademos.org/files/16558/box-model.png)

- **NOTA:** existe un atributo llamado **box-sizing**(sus valores son: *content-box*| *padding-box* | *border-box*). Con el cual le indicamos al navegador que caja tendrá los valores de *width* y *height* del elemento(por defecto este esta en *content-box*).

### **4.4. Propiedad Margin**

- Las propiedades que se encargan de modificar los valores del margen son:
  - **margin-top:** Valor superior(arriba)

  - **margin-right:** Valor derecho

  - **margin-botton:** Valor inferior(abajo)

  - **margin-left:** Valor izquierdo

    ```css
    .box {
        margin-top: 50px;
        margin-right: 100px;
        margin-bottom: 200px;
        margin-left: 30px; 
    }
    ```

- **Shorthand margin** es una propiedad que agrupa a varias:

  - Es en el sentido de las agujas del reloj comenzando arriba, derecha, abajo, izquierda

  - Los valores se completan con sus opuestos , y si hay un solo valor es el mismo para todos 

    | N° de valores | Arriba | Derecha | Abajo | Izquierda |
    | :-----------: | :----: | :-----: | :---: | :-------: |
    |       4       |  1ero  |   2do   |  3ro  |    4to    |
    |       3       |  1ero  |   2do   |  3ro  |    2do    |
    |       2       |  1ero  |   2do   | 1ero  |    2o     |
    |       1       |  1ero  |  1ero   | 1ero  |   1ero    |

  - **NOTA: Los valores pueden estar en pixeles o porcentajes , se hace de la misma forma con padding**

    ```css
    .box {
    	/* 4 valores */
        margin: 50px 100px 200px 100px;
        /* 3 valores */
        margin: 50px 100px 200px ;  
        /* 2 VALORES */
        margin: 50px 100px ; 
        /* 1 VALOR */
        margin: 50px; */
    }
    ```

### **4.5. Dimensiones**

- **DECLARADAS**
  - Cuando se define con width y height
  - Tamaño fijo (width y height)
    - Propiedad box-sizing declarada en border-box
    - Propiedad background-clip: a que caja se aplica el background
  - **PORCENTAJES**
    - Depende del papa
    - Height solo para tamaño definido ,no automáticos(el navegador lo asigna)
    - Donde acaba el contenido acaba el body
    - Las alturas siempre para tamaños definidos
    - **Viewport hight(vh)**, **viewport widht(vw)**, es el porcentaje de la pantalla total (para que se adecue a la pantalla)

- **AUTOMÁTICAS**
  - No se define el alto y ancho `min-widht`, `min-height` , etc, el navegador calcula el tamaño que tendrá al final
  - Se puede aplicar un width con porcentaje pero no un height con porcentaje



## **5. BORDES Y SOMBRAS**

### **5.1. ¿Cómo se dibuja respecto al fondo?**

El borde se dibuja siempre por dentro de la caja, registramos el elemento único externo del modelo box es el margen. **NOTA:** Una buena practica recordemos que es el configurar `box-sizing: border-box;`. De esta manera no evitamos problemas con el maquetado ya que aunque el borde esta por dentro de nuestra caja si no hacemos esta configuración le aumentara las dimensiones a la misma.

- BUENA PRÁCTICA : para que se aplique a todo los elementos:

  ```css
  *, *::before, *::after {
      box-sizing: border-box;
  }
  ```

### **5.2. Propiedades**

Tenemos 3 propiedades básicas

#### **5.2.1.**   **BORDER WIDTH**

Configura el grosor de la linea.

#### **5.2.2.**   **BORDER STYLE**

Indica el estilo que se le aplicara a la linea. Sus posibles valores son:

- none (por defecto).
- hidden.
- solid.
- dotted.
- dashed.
- double.
- groove.
- ridge.
- inset.
- outset.

#### **5.2.3.**   **BORDER COLOR**

EL color de la linea.

### **5.3. Shorthands**

Existen distintos shortand para los border:

1. **Shorthand1:**

   `border:width value style value color value`

   ```css
   .box {
       width: 300px;
       height: 300px;
       color: green;
       background-color: transparent;
       margin: 100px auto;
     
       border: 150px solid green;
   }
   ```

2. **Shorthand 2:**

   - **border-width:** 

     - *width_value_top* 
     - *width_value_right*
     - *width_value_botton* 
     - *width_value_left*

   - **border-style:** 

     - *style_value_top*
     - *style_value_right*
     - *style_value_botton*
     - *style_value_left*

   - **border-color:** 

     - *color_value_top* 

     - *color_value_right* 

     - *color_value_botton* 

     - *color_value_left*

       ```css
       .box {
           width: 300px;
           height: 300px;
           color: green;
           background-color: transparent;
           margin: 100px auto;
           
           border-style: solid;
           border-color: blue transparent transparent;
           border-width: 150px ; 
       }
       ```

3. **Shorthand 3:**

   -  **border-top:** 

     - *width_value_top**
     - **style_value_top* 
     - *color_value_top*

   - **border-right:** 

     - *width_value_right**
     - **style_value_right* 
     - *color_value_right*

   - **border-botton:** 

     - *width_value_botton*
     - *style_value_botton*
     - color_value_botton

   - **border-left:**

     - width_value_left* 

     - *style_value_left* 

     - *color_value_left*

       ```css
       .box {
           width: 300px;
           height: 300px;
           color: green;
           background-color: transparent;
           margin: 100px auto;
           
           border-top: 150px solid blue;
           border-right: 150px solid transparent;
           border-bottom: 150px solid transparent;
           border-left: 150px solid transparent; 
       }
       ```

- **NOTA**: El color del borde siempre es el color de la caja (color: valor) a menos que se declare la propiedad del border-color y asignar otro color.

### **5.4. Border Radius**

Esta propiedad nos permite "recortar" un arco de circunferencia (de 45°) en las esquinas de nuestras cajas.

- La sintaxis es la siguiente:
  - **border-top-left-radius:** *x_radius y_radius*;

  - **border-top-right-radius**: *x_radius y_radius*;

  - **border-botton-right-radius:** *x_radius y_radius*;

  - **border-botton-left-radius:** *x_radius y_radius*

    ```css
    .contenedor {
        --border-radius-x: 300px;
        --border-radius-y: 300px; 
        width: 400px;
        height: 400px;
        background: rgb(163, 26, 26);
        /* SI ES UN CUADRADO Y LE DAMOS 50% SE CONVIERTE EN UN CIRCULO */
        border-radius: 50%;
        border-top-left-radius: var(--border-radius-x) var(--border-radius-y);
        border-top-right-radius: var(--border-radius-x) var(--border-radius-y);
        border-bottom-right-radius: var(--border-radius-x) var(--border-radius-y);
        border-bottom-left-radius: var(--border-radius-x) var(--border-radius-y); */
    }
    ```
  
-  **Shorthand border-radius:**
  - x_radius_top_left 
  - x_radius_top_right 
  - x_radius_botton_right  
  - x_radius_botton_left 
  - y_radius_top_left 
  - y_radius_top_right 
  - y_radius_botton_right 
  - y_radius_botton_left; 

- **NOTA:** Los valores de los radios pueden darse en *px* o en *%*

### **5.5. Outline**

- Funciona muy parecido al borde, con la diferencia que se dibuja por fuera de la caja. 
- Su sintaxis es: `outline: width_value style_value color_value`**. **
- **Usarlo en caso de inspeccionar elementos.**

### **5.6. Box shadow(Sombras)**

- Los sombras son una de las características mas fascinantes de ccs. Todo esta en practicar y experimentar con ellas. 

- **Sintaxis:**`box-shadow: `

  - h-offset(HORIZONTAL) 

  - v-offset(VERTICAL) 

  - blur (DIFUMINADO) 

  - spread (CUANTO SE EXPANDE)

  - color | inset(optional, si la sombra es interior o exterior) 

  ```css
  .box {
      width: 200px;
      height: 200px;
      background: hsl(10, 90%, 50%);
      /* box-shadow: -2px -2px 10px rgba(0,0,0,.5) inset; */
      box-shadow: 0px 0px 0px 10px blue,
      0px 0px 0px 20px green,
      0px 0px 0px 30px yellow
      ; 
      /* box-shadow: 0 50px 0 yellow inset,
      0 100px 0 blue inset,
      0 150px 0 purple inset; */
      box-shadow: 0 8px 10px -3px rgba(0,0,0,.5)
  }
  ```



## **6.**   **FONDOS(BACKGROUND)**

### **6.1. Color**

- **Sintaxis:** `background-color: <color_value>`

- Por buena práctica es mejor declarar el color con background-color 

  ```css
  body {
      background-color: purple;
  }
  ```

### **6.2. Image**

**Sintaxis:** `background-image: url (image.jpg)`

### **6.3. Repeat**

- **Sintaxis:** `background-repeat: value` **(Se usa para background image)**

- Valores:
  - repeat (por defecto)

  - no-repeat (no se repite)

  - repeat-x

  - repeat-y

    ```css
    /*image , repeat*/
    body {
        background-image: url(img/descarga.jpg);
        background-repeat: repeat-x;
    }
    ```

### **6.4. Clip**

- Indica que parte de la caja (context, padding,border) es **cubierta por el fondo**. 
- **Sintaxis:** `background-clip: value`
- Valores: **(Se usa para background image)**
  - border-box (por defecto)
  - padding-box
  - content-box

### **6.5. Origin**

- Indica desde parte de la caja se **comienza a dibujar el fondo**. 
- **Sintaxis:** `background-origin: value`
- Valores: (**Se usa para background image)**
  - border-box (por defecto)
  - padding-box
  - content-box

```css
/*clip and origin*/
.box {
    width: 1450px;
    height: 1400px;
    background-image: url(img/camaleon.jpg);
    background-clip: content-box;
    background-origin: content-box;
}
```

### **6.6. Size**

- Podemos modificar el tamaño a mostrar de una imagen con ccs. 

- **Sintaxis:** `background-size: value` **(Se usa para background image)**. Posibles valores:

  - **widht= height** (un solo valor puede ser en px o %)

  - **widht height** (dos valores pueden ser en px o %)

  - **contain** (ajusta la imagen para que se muestre completa lo más grande posible)

  - **cover** (ajusta la imagen para que se muestre en el 100% de la caja, sin deformar la imagen)

  - **auto** (esta es la opción por defecto, muestra la imagen en su tamaño original)

  ```css
  .box {
      width: 900px;
      height: 900px;
      background-image: url(img/camaleon.jpg);
      background-size: cover;
  }
  ```

### **6.7. Position**

- Esta propiedad es utilizada para especificar desde que coordenada se dibujara la imagen (las coordenadas [0,0] es igual a [left, right]). 

- **Sintaxis:** `background-position: value`

- Se usa para background image, el unit te ayuda a darle valores en px a la imagen**

- Valores:
  - x (y se pone automáticamente, Puede ser en px o %)

  - x y (Puede ser en px o %)

  - **para x: left | center | right <unit>**  **para y: top | center | bottom <unit>**  

  ```css
  .box {
      width: 500px;
      height: 500px;
      background-image: url(https://ed.team/static/images/logo.svg);
      background-position: bottom 20px right 20px;
  }
  ```

### **6.8. Attachment**

- Esta propiedad nos permite fijar la imagen en el fondo. 

- **Sintaxis:** `background-attachment: value`

- Posibles valores:
  - scroll (por defecto)

  - fixed

  - local

    ```css
    .parallax {
        background-image: url(https://c402277.ssl.cf1.rackcdn.com/photos/18134/images/hero_small/Medium_WW226365.jpg?1574452099);
        background-attachment: fixed;
    ```

### **6.9. Multiples**

Es posible tener múltiples fondos en una sola caja. Para manipular las propiedades de cada imagen las dividimos a través de comas (,) comenzando por la url. Ejemplo:

```css
body {
  background-image: url(PATH_image1), url(PATH_image2), url(PATH_image3);
  background-size: 10%, 50 px, containt;

}
```

### **6.10. Shorthands**

La sintaxis del shorthand es la siguiente: 

- `background: image position / size repeat attachment origin clip`
- Los valores pueden ir en cualquier posición menos las propiedades **position / size** estas si deben ir en este orden específico. Position seguido del size separados por un /.



## **7.**   **TEXTOS **

### **7.1. Unidades**

- **em**

  Es el tamaño de fuente del contexto(es variable depende del padre). NOTA: Si el padre es el body, em=rem.

- **rem**

  Es el tamaño de fuente del root(es ctte depende del html)

### **7.2.Alineado de Texto** 

#### **7.2.1. Direction**

- Nos permite cambiar la dirección del texto.( No se usa mucho)
- **Sintaxis:** `direction: value`
- Valores :
  - ltr (left to right)
  - rtl (right to left)

#### **7.2.2. Text- indent**

- Nos Permite modificar la indentacion de la primera linea de un texto.
- **Sintaxis:** `text-indent: value;`
- Valores en px y relativos(em o rem).

```css
body {
    font-size: 2em;
}
p {
    direction: ltr; 
    text-indent: 2em;
}
```

#### **7.2.3.   Text-align**

- Indica la alineacion del texto.
- **Sintaxis:** `text-align: value`

- Valores:
  - start (tiene que ver con direccion- casi no se usa)
  - end (tiene que ver con la direccion-casi no se usa)
  - left
  - center
  - right
  - justify (se considera mala practica. Se ve feo en algunas pantallas)

- NOTA: Existe una propiedad que es **text-align-last** que es para justificar la ultima linea.

  ```css
  body {
      font-size: 2em;
  }
  p {
      text-align: justify;
      text-align-last: right;
  }
  ```

#### **7.2.4.   Line-height**

- **Indica la altura de linea.**

- **Sintaxis:** `line-height: value`

- Los valores pueden ser relativos(em [no hace falta colocar la unidad]) o cttes(px)

- NOTA: los valores pueden ir de 1.3 a 1.6 (em)

  ```css
  div {
      width: 300px;
      height: 300px;
      background-color: yellow;
      line-height: 300px;
  }
  ```

#### **7.2.5.**   **Vertical-align**

- **Sintaxis:** `vertical-align: value`

- Valores:
  - baseline (por defecto)
  - top
  - middle
  - bottom

-  **NOTA:** LAS IMAGENES SON INLINE y actúan como texto se puede alinear un icono con **vertical align** 

  ```css
  span {
      font-size: .5em;
      vertical-align: bottom;
  }
  ```

### 7.3. FLUJO DEL TEXTO

**7.3.1. Letter Spacing (espaciado entre letras) **

- **Sintaxis:** `letter-spacing: Value`

- El valor es relativo o ctte. Positivo o negativo

  ```css
  h1 {
      text-align: center;
      font-family: serif;
      letter-spacing: .3em;
  }
  ```

#### **7.3.2. Word spacing (espaciado entre palabras )**

- **Sintaxis:** `word-spacing: Value`

- El valor es relativo o ctte. Positivo o negativo

### **7.4. Text decoration**

Nos permita dibujar líneas en el texto

**7.4.1.   Line**

- Nos indica el dónde se ubicará la línea.
- **Sintaxis:** `text-decoration-line: value`

- Valores:
  - underline
  - overline
  - line-through
  - none

**7.4.2. Color**

- Nos indica el color de la linea a dibujar.
- **Sintaxis:** `text-decoration-color: value`

**7.4.3.   Style**

- Nos indica el estilo de la linea (igual que en border). 

- **Sintaxis:** `text-decoration-style: value`

- Valores:
  - none.
  - hidden.
  - solid.
  - dotted.
  - dashed.
  - double.
  - groove.
  - ridge.
  - inset.
  - outset.

```css
h1 {
    text-align: center;
    text-decoration-line: line line-through;
    text-decoration-color: red;
    text-decoration-style: solid; 
}
```

**7.4.4.   SHORTHAND**

- **Sintaxis:** `text-decoration: value_line value_style value_color`

- NOTA:** pueden asignarse varios valores de línea (arriba, abajo, tachado)

  ```css
  h1 {
      text-decoration: underline  overline;
  }
  ```

### **7.5. Text shadow**

Es muy similar al shadow de las border. 

**Sintaxis:** `text-shadow: h-offset v-offset blur color.`

```css
h1 {
    text-align: center;
    text-shadow: 2px 2px 2px red;
}
```

### **7.6. White Space (espacios en blanco)**

- Esta propiedad trata del espacio en blanco cuanto tipiamos en el código. nos permite o no escapar los espacios en blanco y los saltos de línea.

- **Sintaxis:** `white-space: value`

- Valores:
  - normal (escapa saltos de línea y espacio en blanco)

  - pre (no escapa nada)

  - nowrap (escapa solo los espacios en blanco)

  - pre-wrap (salta de línea y conserva espacios)

  - pre-line (salta de línea y no conserva espacios)

    ```css
    body {
        font-size: 2.5em;
    }
    p {
        white-space: pre;
    }
    ```

### **7.7. Desbordamiento**

Es útil cuando los textos se 'desbordan' de las cajas que los contiene

#### **7.7.1. Break**

- Divide la palabra y manda el resto a la siguiente línea. 
- **Sintaxis:** `word-break: value`

- Valores:
  - normal
  - break-all
  - keep-all (mantiene a la palabra)

#### **7.7.2. Wrap**

- Manda la palabra a la siguiente línea, sino cabe la pica. 
- **Sintaxis:** `word-wrap: value`

- Valores:
  - normal
  - break-word

#### **7.7.3. Overflow**

- Nos sirve para indicar que el texto continuo, pero no cabe en la caja (colocando 3 puntos). Todo lo que se escapa de la caja se oculta. 

- **Sintaxis**: `overflow:value`                

- Valores:
  - normal

  - break-word

    ```css
    p {
        width: 130px;
        border: 2px solid black;
        /* word-break: break-all; */
        /* word-wrap: break-word; */
        overflow: hidden;
        text-overflow: ellipsis;
    }
    ```

### **7.8. Text-vertical**

Para hacer un texto vertical se combina el modo de escritura vertical: `writing-mode: vertical-lr` con las letras arriba `text-orientation: upright`

### **7.9. Text transform**

- Esta propiedad no sirve para pasar imprimir el texto en mayúsculas o minúsculas.

- **Sintaxis:** `text-transform: value`

- Valores:
  - uppercase (texto en mayuscula)
  - lowercase (texto en minúscula)
  - capitalize (cada palabra del texto comience en mayúscula)

- NOTA: Permite uniformizar los diseños

  ```css
  p {
      writing-mode: vertical-lr;
      text-orientation: upright;
  }
  ```

### **7.10. Fuentes**

Es el tipo de letra

#### **7.10.1. Font-family**

- **Familias tipográficas genéricas:** 

  - serif
  - sans-serif
  - monospace
  - display (para titulos)
  - cursive

- **Sintaxis**: `font-family: option1, ‘option2’, option3, familia_generica`

- Si el nombre de la fuente tiene espacio usar comillas

- Poner al inicio la fuente, luego la otra fuente en caso no cargue la primera, al final la familia genérica.

  ```css
  body {
      font-size: 8em;
      font-family: 'Times New Roman', Georgia, serif;
  }
  ```

#### **7.10.2. Font-size(tamaño)**

- **Sintaxis:** `font-size: value`

- Valores:
  - porcentaje
  - pixeles
  - em
  - rem

  ```css
  span {
      font-size: 4rem;
  }
  ```

#### **7.10.3. Font-weight(Grosor del trazo)**

- **Sintaxis:** `font-weight: value`

- Valores: 
  - bold
  - normal
  - lighter
  - bolder
  
- **NOTA**: No es recomendable utilizar las palabras como valores. Lo recomendado es utilizar múltiplos de 100 comprendidos entre 100 y 900

  ```css
  body {
      font-family: 'IBM Plex Serif', serif;
      font-weight: var(--tamaño);
      /* FONT STYLE */
      font-style: italic;
      /* TODAS MAYUSCULAS PERO LA PRIMERA LETRA UN POCO MAS GRANDE */
      font-variant: small-caps;
  }
  ```

#### **7.10.4. Shorthand font**

- **Sintaxis:** `font: font-family font size /weight`

- **NOTA:**
  
  - El font-family siempre va al final
  
  - Font- family y font size deben existir los demás son opcionales
  
    ```css
    article {
        /* FONT SIZE Y FONT FAMILY OBLIGATORIOS */
        font: 5em /1.5 verdana;
    }
    ```
  
    

## **8. PSEUDOCLASES **

Estilos especiales que van a depender dentro del contexto, posición o estado que se encuentren los elementos HTML. Se coloca un par de dos puntos **(:)** ejem: **:root** . 

### **8.1. Root**

**(:root)** La pseudoclase **:root** selecciona el elemento raíz de un documento. Aplicado a HTML, :root representa el elemento `<html>` y es idéntico al selector html, excepto que su nivel de especificidad es mayor que HTML. Sirve para variables CSS.

### **8.2. Hover**

La pseudoclase de CSS **:hover** se presenta cuando el usuario coloca el puntero sobre algún elemento, pero no necesariamente está activo. En pantallas táctiles no es recomendable.

```css
[type="submit"]:hover{
    background-color: var(--dark-color);
}               
```

### **8.3. Active**

- La pseudoclase de CSS **:active** .Corresponde al momento en el que el usuario presiona el raton hasta el momento en que lo suelta. A menudo es usado en los elementos `<a>` y `<button>` de HTML. 

- NOTA : El orden si importa al momento de declarar las siguientes Pseudo-clases: **Tiene    que ir en este orden la pseudoclases (regla de cascada)**    

  - `link {...}`    

  - `visited {...}`    

  - `hover {...}`   

  - `active {...}`            

    ```css
    .Main article:active {
        background-color: var(--second-color);
        color: var(--dark-color)
    }
    ```

- **Pseudoclases:**
  - `link` :  se aplica a todos los enlaces que todavía no han sido visitados por el usuario.
  - `visited`: se aplica a todos los enlaces que han sido visitados al menos una vez por el usuario.

### **8.4. Target** 

La pseudoclase de CSS :target representa el elemento único, si existe alguno con un id coincidente con el identificador de fragmentos de la URL del documento `(href="#idOfElement")`

```html
<a href="#modal">Modal con CSS</a>
<div id="modal" class="Modal">
    <h2>Hola soy un modal con CSS</h2>
</div>
```

```css
.Modal:target {
    display: flex;
}
```

### **8.5. Child**

- **nt-child(:nth-child)** :selecciona el elemento indicado que sea el enésimo hijo de su elemento padre

  - nth-child(3n): este permite manejar expresiones, cada 3 elementos se aplican los estilos
  - nth-child(odd): este permite aplicar los estilos a los elementos pares
  - nth-child(even): este permite aplicar los estilos a los elementos impares

  ```css
  .Main article:nth-child(even):active {
      background-color: var(--second-color-alt);
      color: var(--dark-color-alt);
  ```

- **first-child (:first-child)** : selecciona el elemento indicado que sea el primer hijo de su elemento padre.

- **last-child (:last-child)** : selecciona el elemento indicado que sea el último hijo de su elemento padre.

### **8.6. Of-type**

- **nth-of-type(:nt-of-type):** Selecciona el elemento indicado que sea el enésimo hijo en su tipo sin importar la jerarquia dentro del elemento padre
- **first-of-type(:first-of-type):** Selecciona el elemento indicado que sea el primer hijo en su tipo sin importar la jerarquia dentro del elemento padre
- **last-of-type(:last-of-type):** Selecciona el elemento indicado que sea el ultimo hijo en su tipo sin importar la jerarquia dentro del elemento padre

### **8.7. NOT**

La pseudoclase CSS de negación , **:not(X),** es una notación funcional que toma un selector simple que toma a X como argumento. Permite negar u omitir los estilos al argumento dentro de la pseudoclase not

```css
[type]:not([type="submit"]) {
    margin-bottom: .5rem;
    padding: .5rem;
    border: thin solid var(--second-color);
    background-color: var(--body-bg);
    color: var(--first-color);
}
```

### **8.8. Empty**

La pseudoclase **:empty** aplica los estilos a cualquier nodo que no tenga contenido ni nodos textuales, etiquetas, sin ningún nodo hijo.

```css
p:empty {
    margin-bottom: 0;
    disp
```

 

## **9.   PSEUDOELEMENTOS**

- Toda etiqueta html es un elemento.


- Los pseudoelementos son un tipo de "elementos falsos" pues en realidad estos no existen en el árbol DOM(árbol de documentos), sin embargo podemos manipularlos con CSS.
- **Son representados por el nombre del elemento, seguido de 2 dobles punto(::)** y luego el nombre del Pseudo-elemento. Existen varios, algunos de ellos son:

### **9.1. First-line**

- Es útil en textos y como su nombre lo indica hace referencia a la primera linea de texto mostrada en pantalla. 

- **Sintaxis:** `first-line{ ... }`

- NOTA: **solo aplica para elementos de bloque. Principalmente para ejemplos creativos.**

  ```css
  h1::first-line {
  	text-transform: uppercase;
  	font-size: 2em;
  }
  ```

### **9.2. First-letter**

- Es útil en palabras o textos y hace referencia a la primera letra del texto mostrado en pantalla.

- **Sintaxis:** `::first-letter { ... }`

- **float: left** permite tirar un elemento a la izquierda o derecha rompiendo el flujo

- NOTA: **solo aplica para elementos de bloque, no para elementos inline (span,a,etc)** 

  ```css
  p:last-child::first-letter {
  	color:red;
  	margin-right: .1em;
  	float: left;
  }
  ```

### **9.3. Before and After** 

- El contenido debe ser generado antes de ser manipulado. **(contenido generado)**

- **Propiedad Content:**

  - Imprimir un string en el elemento (etiqueta) seleccionado. **Ejemplo :**

    ```css
    h1::before {
    	content: '¿'
    }
    h1::after {
    	content: ''?'
    }
    ```

  - Imprimir atributos con `attr().` Se imprime el contenido (atributo) de la clase.

    - **NOTA**: debe tener un `content` y un `display block`

    ```css
    <h1 class="ed-team"> Que es EDteam></h1>
    h1::before {
    	content: attr(class);
    	display: block;
    }
    ```

  - Imprimir imágenes con `url()`: Inserta la imagen de la ruta del elemento

    ```css
    h1::before {
    	content: url(https://ed.team/static/images/logo.jpg);
        height: 100px;
    }
    ```

  - Imprimir comillas de citas (quotes)

    ```css
    h1 {
    	quotes: '"' '"';
    }
    h1 {
        /*Establece caracteres de abrir y cerrar de las citas */
        quotes: '\201C' '\201D'
    }
    
    h1::before {
        content: open-quote;
    }
    h1::after {
        content:close-quote;
    }
    ```

- **Son elementos inline por defecto**. Pero se puede cambiar para convertirlo en un elemento de bloque con **display(block).**

  

## **10.   LISTAS Y CONTADORES**

### **10.1.Listas**

- **Nota:** Podemos lograr que cualquier elementos "parezca" una lista con la propiedad `display: list-item`.

  ```css
  span {
  	display: list-item
  }
  ```

- Las listas tienen 3 propiedades en CSS:
  -  **List-style-type**

    Se refiere al tipo de viñeta que se le colocara o precederá a los elementos de las listas. **Su sintaxis es**: `list-style-type: value`

    - Posibles valores:

      - disc (circulo relleno)

      - circle (circulo hueco)

      - square (cuadrado relleno)

      - decimal (números)

      - decimal-leading-zero (numero con un cero por delante)

      - lower-alpha (letras minúsculas)

      - upper-alpha (letras mayúsculas)

      - none (le quita cualquier marcador)

        ```css
        ul,ol {
        	list-style-type: disc;
        }
        ```

  - **List-style-image**

    Existe una propiedad list-style-image pero es mala practica utilizarla. Es **recomendable utilizar el pseudo-elemento `::before` y colocar la imagen en su background.**

    ```css
    ul,ol {
    	list-style-type: none;
    }
    li::before {
    	content: '';
    	display: inline-block;
    	background-image: url(icon.png);
    	background-size: contain;
    	width: .8em;
    	height: .8em;
    }
    ```

  - **List-style-position**

    - Esta propiedad indica si las propiedades están por fuera de los `<li>` o por dentro. **Sintaxis: `list-style-position: value`

    - Posibles valores: inside (dentro de los <li>

      ```css
      ul,ol {
      	padding-top: 10px;
      	list-style-position: inside;
      }
      ```

### 10.2. Contadores

- Los contadores en css son muy parecidos a los contadores en un lenguaje de programación. Hay varias cosas a tener en cuenta:

  1. Deben ser declarados(en la propiedad **counter-reset:**), `counter-reset: nombre` Este crea un contador y lo resetea y al valor del contador le damos un nombre cualquiera
  2. Existen en el Scope que se les declara.
  3. Se incrementan con la propiedad `counter-increment: nombre del contador` 

- **Nota 1:** Para imprimir el contador y concatenarlo con un String usamos la función de : `content: counter()` que recibe **dos parámetros** el primero es el **nombre del contador** y el segundo es un **string('.'**) con el separador.

  ```css
  /* INICIALIZA ,DECLARA Y RESETEA EL CONTADOR EN EL CONTENEDOR */
  .chapters{
      counter-reset: chapter;
  }
  /* INCREMENTAMOS EL VALOR DEL CONTADOR  EN CADA ELEMENTO DE LA CLASE CHAPTER  */
  .chapter{
      counter-increment: chapter;
  }
  /* IMPRIMIMOS EL CONTADOR CON COUNTER(NOMBRE_CONTADOR), LE DAMOS ESTILO A LAS VIÑETAS */
  .chapter::before {
      content: counter(chapter) ". ";
      color:red;
  }
  ```

- **Nota 2:** Para imprimir el contador en listas anidadas utilizamos **la función **`content : counters()` que recibe d**os parámetros** el primero es el **nombre del contador** y el segundo es un **string('')** con el separador.

  ```css
  /* INICIALIZA ,DECLARA Y RESETEA EL CONTADOR EN EL CONTENEDOR */
  .chapters{
      counter-reset: chapter;
  }
  /*INCREMENTAMOS EL VALOR DEL CONTADOR  EN CADA ELEMENTO DE LA CLASE CHAPTER */
  .chapter{
      counter-increment: chapter;
  }
  /* IMPRIMIMOS EL CONTADOR CON COUNTER(NOMBRE_CONTADOR), LE DAMOS ESTILO A LAS VIÑETAS */
  .chapter::before {
      content: counter(chapter) ". ";
      color:red;
  }
  
  ol {
      counter-reset: lista;
      list-style: none;
  }
  
  li {
      counter-increment: lista;
  }
  
  li::before {
      content: counters(lista , ".") ". ";
      color: red;
      margin-right: 0.3em;
      font-size: 1em;
  }
  ```

  

## **11.   COLOR Y DEGRADADOS**

### **11.1. Variables**

- COLOR: Esta propiedad se refiere al color del texto.

- BACKGROUND: Este es un shorthand que tiene varias propiedades de background como color, position, size, etc

- BACKGROUND-COLOR: Esta propiedad es el color de fondo

- CURRENTCOLOR: En CSS es una variable(se puede decir que es de las primeras que existió en el lenguaje), que hace **referencia al color actual que tiene el elemento de la propiedad color.**


### **11.2. Color Keywords**

Existen diferentes y muy variados keyword para los colores puedes verlos acá:

- Colores Básicos (https://www.w3.org/wiki/CSS/Properties/color/keywords)

- Colores X11(https://en.wikipedia.org/wiki/X11_color_names)

- Transparent (cuando no quieres un color y quieres que sea transparente)


### **11.3. Modo de color RGB**

-  **Características:**
  - Para pantallas el modo RGB es un modo de color aditivo(de luz).

  - Se basa en 3 canales; Red(R), Green(G), Blue(B).

  - Su valores van de 0 a 255 (2^8, 1 Byte).

  - Los 3 canales en 255 dan blanco.

  - Los 3 canales en 0 dan negro.

  - Los 3 canales en el mismo nivel dan un tono de gris.

    ```css
    body {
    	background-color: rgb(0,255,255); 
    }
    ```

- **Diferencia entre RGB y RGBA**
  - rgb(R,G,B)

  - rgba(R,G,B,A) La única diferencia es que RGBA tiene un valor adicional que hace referencia A:

    - alpha(transparencia), este valor va de 0 a 1(es un float).

      ```css
      body {
      	background-color: rgba(79, 100, 138, 0.5); 
      }
      ```

- **Notación Hexadecimal**
  - Es otra forma de denotar el modo de color: **#RRGGBB**

  - Cada par de caracteres representa un canal.

  - Si los dos caracteres de un canal se repiten puede abreviarse: **#AA00EE = #A0E**

  - Los valores van de 0 a F

    - A, B, C, D, E, F representa 10, 11, 12,13,14,15

    - 2^8= 2^4*2^4=16*16 

      ```css
      body {
      	/* background-color: #0FF; */
          background-color: #00ffff;
      }
      ```

### 11.4. Modo de color HSL

- **Importante**: HSL no es HSB.

- **¿Que significa el acrónimo?**

  -  **Hue** (tonalidad de color, de 0 a 360, circulo cromático). 0=RED 120=GREEN 240=BLUE

    - *COLORES*
      - **0/360 : red**
      - 60: yellow
      - 120: **green**
      - 180: cyan
      - **240: blue**
      - 300: magenta

  - **Saturación** (intensidad del color, de gris [0%] , al color puro [100%]).

  - **Luminosidad** (de negro [0%], color puro (color real) [50%], blanco [100%]).

    ```css
    body {
        background-color: hsl(350, 90%, 60%); 
    }
    ```

- **Notación HSL Y HSLA**

  - hsl(numero, porcentaje, porcentaje)

  - hsla(numero, porcentaje, porcentaje, transparencia[de 0 a 1 en decimal])

    ```css
    body {
    	background-color: hsla(350, 90%, 60%, .67);
    }
    ```

### 11.5. Degradados

En esencia **son IMÁGENES**. Por lo tanto cuenta con todas sus propiedades(background-size, position, etc).

1. **Lineales**

   -  Sintaxis(lo que esta entre [] son parámetros opcionales):

     - `linear-gradient([angle deg], color1 [stop], color2[stop], ..., colorN[stop])`

       ```css
       body {
           min-height: 100vh;
           background: linear-gradient(yellow,red);
           /* ANGULO  */
           background: linear-gradient(90deg , yellow,red); 
           /* ANGULO POR KEYWORDS */
           background: linear-gradient(to right , yellow,red);
           background: linear-gradient(to top right , yellow,red); 
       }
       ```

   - **Parámetros opcionales:**

     1. **Angulo**
        - **Por valor**
          - Por defecto es top-bottom
          - 0(bottom-top). Avanza en sentido horario.
          - *90 deg*  (left-right)
          - *180 deg* (top-bottom)
          - *270 deg* (right-left )
        - **Por keywords**
          - to[top|right|bottom|left]
          - to[top left|top right|bottom left| bottom right]

     2. **Stops**

        Son un porcentaje o tamaño fijo, e indican en donde el color se empieza a degradar. Ejemplo:

        ```css
        body {
            /* SON IMAGENES ASI QUE TIENEN LAS MISMAS PROPIEDAD  */
            min-height: 100vh;
            background: linear-gradient(red 50%,blue);
        }
        ```

   - **Repeat**

     - **Sintaxis**: `repeating-linear-gradient([angle deg], color1 [stop], color2[stop], ..., colorN[stop])`

       ```css
       body {
          min-height: 100vh;
          background-image: repeating-linear-gradient(yellow 30px, red 60px)
       }
       ```

2. **RADIALES**

   - **Sintaxis:** `background-image: radial-gradient([size shape], [at xcenter ycenter], color1 [stop1], color2 [stop2], ..., colorN [stopN])`

   - **Nota:** el AT xcenter ycenter es para ubicar la posición y su valor es en **%**

     ```css
     body {
         background-image: radial-gradient(closest-corner circle,yellow,red, 	cyan,purple);
     }
     ```

     1. **Shape**

        Tiene dos posibles valores:

        - circle|elipse
        - Si se omite ,la forma se calcula por el tamaño del elemento.

     2. **Size**
        - Pueden ser unidades fijas o relativas(x y)
        - Keywords que podemos utilizar
          - closest-side (el lado mas cercano)
          - farthest-side(el lado mas lejano)
          - closest-corner(esquina mas cercana)
          - farthest-corner(esquina mas lejano)

   -  **Repeat**

     - **Sintaxis**: `repeating-radial-gradient([size shape], [at xcenter ycenter], color1 stop1, color2 stop2, ..., colorN stopN)`

       ```css
       body {
           background:repeating-radial-gradient(circle ,white 0,white 			20px, red 20px,red 40px) ;
       
       }
       ```

       

## **12. POSITION**

- Nos permite alterar e flujo normal de los elementos.


- **Nota**: Todos los elementos en un inicio son `position static`

### **12.1. Propiedades de Offset**

- **Mueven un elemento posicionado **según el borde indicado, 

- **Sintaxis:**

  - Donde se empieza a mover , es el lado donde se toma como referencia para mover un elemento , (+) derecha , (-) izquierda, (+) abajo, (-) arriba

  - `top: value`

  - `right: value`

  - `left: value`

  - `bottom: value`

    ```css
    h1 {
        border-top: 1px solid #000;
        top:20px
    }
    ```

### **12.2. Valores de posición** 

- **Static**

  **Es el valor por defecto que tienen los elementos**, Mantienen el posicionamiento por el flujo del HTML. A los elemento con ese valor no se les considera posicionados.

- **Relative**

  Se le llama elemento posicionado. Características:
  - Su referencia es su posición inicial.

  - Aplicar position relative a un elemento no modifica en nada su layout.

  - Al moverlo, con las propiedades offset, reserva su espacio.

    ```css
    .p3 {
        color: blue;
        position: relative;
        bottom: 2em;
    }
    ```

- **Absolute**

  Se le llama elemento posicionado . Características:
  - Pierde su posición en el flujo y no reserva su espacio.

  - Si tenia dimensiones fijas se mantienen, si tiene dimensiones automáticas; se ajustaran a su contenido.

  - **Su referencia es su ancestro posicionado mas cercano.**

  - **Se mueve respecto a su ancestro que tenga cualquier posicionamiento ya sea absolute, relative, fixed, etc**

    ```css
    .box {
        /* BUSCA CUALQUIER POSICIONAMIENTO DEL PAPA */
        position: relative;
        width: 500px;
        height: 500px;
        background-color: yellow;
    }
     span {
         position: absolute;
         display: block;
         bottom: 0;
         right: 0;     
     }
    ```

- **Fixed**

  Se le llama elemento posicionado. Características:
  - Fijo(no se mueve con el scroll), relativo al viewport.

  - Se ignora en el flujo.

  - Sus dimensiones automáticas se restringen a su contexto.

    ```css
    .main-header {
        background-color: yellow;
        position: fixed;
        width: 100%;
        top: 0;
        height: 3rem;
    }
    ```

- **Sticky**

  - Se le llama elemento posicionado .

  - Es una combinación de Relative y Fixed. 

  - En este caso el offset indica en que instante el elemento pasara a ser fijo en pantalla. Ejemplo para un top: 10px. El elemento será fijo cuando al hacer scroll este saliendo de pantalla, y se mantendrá a 10px del viewport en su parte superior.

    ```css
    h2 {
        position: sticky;
        top: 10px;
        background-color: #fff;
    }
    ```

    

## **13.Z-INDEX**

- La z-index propiedad especifica el orden de apilamiento de un elemento.

- El ultimo elemento en el html aparece siempre arriba dibujado. 

- Todos los elemento de manera automática tienen z-index en 0

- **Sintaxis:** `z-index: value`

- Para elementos con igual z-index se sobrepondrán aquellos que aparezcan después en el flujo(código HTML) como ultimo elemento.

- **Estructura recomendada z-index:**

  - z-back : para mandar un elemento atrás

  - z-normal: volver un elemento al flujo normal,

  - z-tooltip: una alerta en el formulario o tooltip

  - z-fixed: cuando necesitas un elemento fijo en el DOM

  - z-modal:para un modal

    ```css
    :root {
        --z-back:-10;
        --z-normal:0;
        --z--tooltip:10;
        --z--fixed:100;
        --z--modal:1000;
    }
    ```

- **Elementos aplicables:**

  - Elementos posicionados.
  - Elementos Transformados.

- **Nota**: si el papa tiene un z-index declarado el/los hijo(s) no pueden posicionarse detrás de el.