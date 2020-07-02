# **CSS Avanzado Grid + Flexbox**

## **1. FLEXBOX**

- Es una manera de diseñar con CSS. Su principal función es de alineación. Si bien podemos realizar algo del layout con este, solo podemos hacerlo en un solo eje(main axis). Utiliza siempre la **relacion padre e hijos**, no puede existir un flexbox sin este contexto. Los elementos padre son llamados **flex container** y tienen la propiedad **display: flex** , los elementos hijos son **flex item**.

### **1.1. EJES**

Tenemos dos ejes principales:

- **main axis(eje principal)**: De manera predeterminada el eje principal es horizontal, de izquierda a derecha.

- **cross axis( eje transversal**) : De manera predeterminada es vertical, de arriba hacia abajo.

  - **main size | cross size**
  - **main start | main end**
  - **cross start | cross end** 

  ![img](https://www.w3.org/TR/css-flexbox-1/images/flex-direction-terms.svg)

### **1.2. FLEX CONTAINER (PADRE)**

#### **1.2.1 Display**

El flex container(El padre) tiene dos opciones en su display:

1. `display: flex`. Se comporta como un elemento de bloque.

2. `display: inline-flex`. Se comporta como un elemento de linea.

   

   ```css
   .flex-container {
       background: yellow;
       /* el padre se comporta como elemento de bloque */
       display: flex;  */
       /* el padre se comporta como elemento de linea */
       /*display: inline-flex;*/
   }
   
   .flex-item {
       border: 1px solid #000;
       margin: 1rem;
   }
   ```

#### **1.2.2 Flex-direction**

Flex-direction nos permite especificar la dirección y el sentido del eje principal:

- Sintaxis

  ```css
  flex-direction: value;
  ```

  ![img](https://miro.medium.com/max/529/1*p9RKQ08zFMn01OOUkPoa1g.png)

- Valores posibles
  
- row (Predeterminado)
  
- row-reverse (Horizontal, de derecha a izquierda)
  
- column (Vertical, de arriba a abajo)
  
- column-reverse (Vertical, de abajo a arriba)
  
    
    
    ```css
    .flex-container {
        display: flex;
        background: yellow;
        /* su valor por defecto es row */
        flex-direction: column /*de arriba abajo; */
        /* flex-direction: column-reverse; de abajo hacia arriba */
    }
    .flex-container2 {
        display: flex;
        background: rgb(247, 87, 47);
        /* flex-direction: row;  izquierda a derecha */
        /* de derecha a izquierda*/ 
        flex-direction: row-reverse;
    }
    ```

#### **1.2.3 Flex-wrap**

Esta propiedad nos especifica si el flexbox puede o no saltar de linea. Define si los elementos de flexbox aparecen en una sola línea o en varias líneas dentro de un contenedor de flexbox.

- Sintaxis

  ```css
  flex-wrap: value
  ```

- Posibles Valores
  - nowrap(los hijos no pueden saltar de linea. Por defecto)

  - wrap (los hijos pueden saltar de linea) //single line or multi line

  - wrap-reverse (los hijos pueden saltar de linea. Las lineas estan en el orden opuesto[el eje trasversal esta en reversa]).

    ```css
    /*  evitamos el desbordamiento de los elementos con wrap*/
    .flex-container {
        width: 15em;
        height: 15em;
        display: flex;
        background: yellow;
        flex-direction: column;
        flex-wrap: wrap;
    }
    .flex-container2 {
        display: flex;
        background: rgb(247, 87, 47);
         flex-direction: row;
        flex-wrap: wrap;
        /*flex-wrap: wrap-reverse;*/
    }
    ```

#### **1.2.4 Flex-flow**

Es un shorthand que une a *flex-direction* y a *flex-wrap*.

Sintaxis: `flex-flow: value_direction value_wrap`

```css
.flex-container2 {
    display: flex;
    background: rgb(247, 87, 47);
    /* flex-direction: row; */
    /* flex-wrap: wrap; */
    /* shortand para direction y wrap */
    flex-flow: row wrap;
}
```

#### **1.2.5 Alineacion**

- **Alineacion de Items**

  - **Justify-content**

    **Alinea los Items en el eje principal(main axis)** Sintaxis: `justify-content: value`

     Valores:

    - flex-start (Predeterminado) : Los elementos de flexbox se empujan hacia el inicio del eje principal del contenedor.

    - flex-end :  Los elementos de flexbox se empujan hacia el final del eje principal del contenedor.

    - center :  Los elementos de flexbox se empujan hacia el centro del eje principal del contenedor.

    - space-between

    - space-around:  Distribuye items uniformemente. Los items flex se alinean uniformemente de tal manera que el espacio entre dos items adyacentes es el mismo. El espacio vacío anterior al primer item y posterior al último item equivale a la mitad del espacio entre dos items adyacentes.

    - space-evenly : Es similar al space around pero proporciona un espacio igual.

      ![Getting Started with CSS Flexbox Basics - Laina Karosic - Medium](https://miro.medium.com/max/434/1*iigDGiNFBOUVJQ_07C1B2g.png)

  - **Align-items**

    Alinea los Items en el eje transversal(cross axis) dentro de la linea . Sintaxis: `align-items: value`

    Tenemos el valor de nowrap.

    Valores:
  
    - flex-start (Predeterminado) :  : Los flexbox items se alinean al comienzo del  cross start
  
    - flex-end : Los flexbox items se alinean al fnal del eje transversal. cross end
  
    - center :  : Los flexbox items se alinean en el cross axis
  
    - baseline : Los elementos de flexbox están alineados en la línea de base del eje transversal. Por defecto, el eje transversal es vertical . Esto significa que los elementos de flexbox se alinearán para que la línea base de su texto se alinee a lo largo de una línea horizontal.
    
    - stretch : Las elementos son estirados de modo que el tamaño transversal de sus límites sea el mismo del contenedor, manteniendo sus restricciones de anchura y altura. Valor por defecto
    
      ![introducir la descripción de la imagen aquí](https://i.stack.imgur.com/N5Nh7.png)
  
- **Alineacion de Lineas**

  - Align-content

    Define cómo se alinea cada línea dentro de un contenedor flexbox . Solo se aplica si flex-wrap: wrap está presente y si hay *varias líneas de elementos de flexbox*. Alinea las lineas respecto al container . 

    Sintaxis: `align-content: value`

    Posibles valores:

    - flex-start (Predeterminado)
    
    - flex-end 
    
    - flex-center
    
    - space-between : Cada línea solo llenará el espacio que necesita. El espacio restante aparecerá entre las líneas.
    
    - space-around: Cada línea solo llenará el espacio que necesita. El espacio restante se distribuirá equitativamente alrededor de las líneas: antes de la primera línea, entre las dos y después de la última.
    
    - stretch : Cada línea se estirará para llenar el espacio restante.
    
    - space-evenly 
    
      ![introducir la descripción de la imagen aquí](https://i.stack.imgur.com/ZPDMz.png)

### 1.3. FLEX-ITEMS

Los siguientes elementos son catalogados como ítems:

- Hijos directos.
- Pseudoelementos.
- Texto

#### **1.3.1 Flex ítems posicionados**

Los elementos posicionados con absolute o fixed tienen las siguientes características:

- No participan en el flujo.
- Son afectados por las propiedades de alineación del container.

#### **1.3.2 Crecimiento o reducción**

Los flex ítems pueden crecer(grow) o reducirse(shrink). Algo a tener en cuenta es que los márgenes y paddings no se contraen

#### **1.3.3 Propiedades**

##### **1.3.3.1 flex-grow**

Flex-grow Indica el factor de crecimiento. 

- El Navegador Calcula el espacio disponible. Tomando en cuenta el tamaño inicial de cada elemento.
- El navegador divide el espacio disponible entre la cantidad total de los factores de crecimiento.
- Se le asigna a cada elemento el tamaño correspondiente a la cantidad de factores de crecimiento establecidas para el mismo.
- **Sintaxis**: `flex-grow: valor_del_factor_de_crecimiento`
- Valores Posibles:
  
  - Numero positivos(enteros o decimales). Por defecto es 0.
  
##### **1.3.3.2 flex-shrink**

Flex-shrink Indica el factor de reducción.

- El Navegador Calcula el espacio sobrante. Tomando en cuenta el tamaño inicial de cada elemento.
- El navegador divide el espacio sobrante entre la cantidad total de los factores de reducción.
- Se le reduce a cada elemento el tamaño correspondiente a la cantidad de factores de reducción establecidos para el mismo.
- **Sintaxis**: `flex-shrink: valor_del_factor_de_reduccion`
- Valores Posibles:
  - Numero positivos(enteros o decimales). Por defecto, se distribuye uniformemente entre todos los elementos.

##### **1.3.3.3 flex-basis**

Define el **tamaño inicial en el eje principal** puede ser width o height dependiendo del caso.

- **IMPORTANTE:** *Cuando esta asignado ignora la propiedad width o height*(dependiendo del caso de como este 	configurado el eje principal).
- **Sintaxis**: `flex-basis: value`
- Posibles valores:
  
  - Recibe los mismos valores que una propiedad *size*.
  
  - flex-basis: auto: El elemento tendrá el tamaño automáticamente en función de su contenido, o en cualquier `height`o `width`valor si se definen.
  
  - Ejm: flex-basis: 80px : Puede definir valores de **píxeles** o **(r) em** . El elemento envolverá su contenido para evitar cualquier desbordamiento.
  

##### **1.3.3.4 Flex**

- Flex es un shorthand que agrupa a **flex-grow**, **flex-shrink** y **flex-basis**
- **Sintaxis:** `flex: value-grow value-shrink value-basis`
- **Keywords:**
  - initial (0 1 auto). Estos son los valores por defecto.
  - auto(1 1 auto)
  - none(0 0 auto)
  - n (n 0 0). Siendo *n* un numero positivo.

##### **1.3.3.5 aling-self**

- Nos sirve para linear un ítems en especifico respecto al eje secundario. Lo podríamos utilizar en conjunto con la pseudoclase *nth-child()*.
- **Sintaxis**: `align-self: value`
- Valores Posibles:
  - auto(por defecto. Sigue el flujo definido en el contenedor)
  - flex-start
  - flex-end
  - center
  - baseline
  - stretch

##### **1.3.3.6 Order**

- Nos permite colocar un elemento en la parte que deseemos. Sin importar el flujo del HTML.
- Se parece un poco a un *z-index*. Por defecto todos los elemento tienen un order:0.
- **Sintaxis**: `order: value`
- Valores posibles:
  - Cualquier numero entero.

## **2. GRID**

- Layout: geometría que calcula el navegador para saber donde colocar cada elemento y que tanto separarlo de los demás.

- Permite construir layouts a través de dos ejes(horizontal y vertical | inline y block)).

- No importa la posición de un elemento en el código HTML para construir el layout.

- Requiere un relación de padre(grid-container) e hijos(grid-ítems)

  <img src="https://webkit.org/wp-content/uploads/grid-concepts.svg" alt="CSS Grid Layout: A New Layout Module for the Web | WebKit" style="zoom: 67%;" />

  ### [Grid Properties Table of Contents](https://zcfy.cc/original/a-complete-guide-to-grid-css-tricks#grid-table-of-contents)
  
  Properties for the Grid Container
  
  - display
  - grid-template-columns
  - grid-template-rows
  - grid-template-areas
  - grid-column-gap
  - grid-row-gap
  - grid-gap
  - justify-items
  - align-items
  - justify-content
  - align-content
  - grid-auto-columns
  - grid-auto-rows
  - grid-auto-flow
  - grid
  
  Properties for the Grid Items
  
  - grid-column-start
  - grid-column-end
  - grid-row-start
  - grid-row-end
  - grid-column
  - grid-row
  - grid-area
  - justify-self
  - align-self

### **2.1 . GRID-CONTAINER**

#### **2.1.1 Display**

1. `display: grid`.(Visualmente no altera en nada al elemento, es como si aplicáramos un position:relative). Es un elemento de bloque

2. `display: inline-grid`. Elemento de línea


### **2.2. ELEMENTOS ABSTRACTOS (no existen en el DOM)**

- El navegador los crea para posicionar y alinear elementos.
- Son definidos en las propiedades del grid-container.

#### **2.2.1 Grid-tracks**

Son las filas y las columnas. **Forman parte del grid-container**

##### **2.2.1.1 Columnas**

- Sintaxis: `grid-template-columns: width_column1 width_column2 ... width-columnN`
- Los valores admitidos:
  - Son cualquier valor para definir tamaño(em, rem. px, %).
  - fr: Son definidos como valores fraccionarios. Tienen un comportamiento muy similar al valor de flex-grow.

##### **2.2.1.2 Filas**

- Sintaxis: `grid-template-rows: width_row1 width_row2 ... widthrowN`
- Los valores admitidos:
  - Son cualquier valor para definir tamaño(em, rem. px, %).
  - fr: Son definidos como valores fraccionarios. Tienen un comportamiento muy similar al valor de flex-grow.

##### **2.2.1.3 Gap**

Especifican la separación entre columnas o filas respectivamente: 

- Columnas: `column-gap: value` 
- Filas: `row-gap: value`
- Posibles valores:
  - Unidades fijas o relativas.
- Shorthand: `gap: value_row value_column` 

#### **2.2.2 Grid-lines**

Se encuentran a los lados de los tracks:

- Izquierda y derechas para **columnas**.
- Arriba y abajo para **filas**.


#### **2.2.3 Grid-cells**

La Intersección entre una fila y una columna.

#### **2.2.4 Grid-areas**

Cualquier área rectangular delimitada por 4 *grid-lines*

### **2.3.  GRID-ITEMS**

Se consideran como grid-ítems a los:

- Hijos directos
- Pseudoelementos ::before y ::after
- Texto

#### **2.3.1 Posicionamiento**

- Con css-grid podemos colocar un elemento donde queramos. Esto lo hacemos especificándole la línea donde inicia y donde termina dicho elemento. Para esto utilizamos las propiedades:
  -  `grid-column-start: value` (Linea vertical inicial)

  - `grid-row-start: value` (Linea horizontal inicial )

  - `grid-column-end: value` (Linea vertical final)

  - `grid-row-end: value` (Linea horizontal final )

  - **Shorthand**:

    -  `grid-row: value_start / value_end`

    - `grid-column: value_start / value_end`

    - Nota: también podemos contar columnas o filas, utilizando las unidad *'span'*. 

      ```css
      .item-c {
        grid-column: 3 / span 2;
        grid-row: third-line / 4;
      }
      ```

  - **Shorthand:**

    - `grid-area : grid-row-start / grid-column-start / grid-row-end / grid-column-end`

- **NOTA1:** Los grid-items pueden ser a su vez grid-containers.
- **NOTA:2** Los grid container también manejan las propiedades ***justify-content* y *aling-items*.**

### **2.4**.  ALINEACIÓN

#### **2.4.1 Container**

Estas propiedades las utilizamos para mover la alineación de los tracks respecto al contenedor. Las propiedades son muy parecidas a las de flex.

- **En horizontal(x o inline)** tenemos las propiedades:

  - `justify-content` :  alinea toda la cuadrícula dentro del contenedor a lo largo del row axis

    - `justify-content: start`  

      ![Example of justify-content set to start](http://p0.qhimg.com/t011c175bd21bd04873.png)

    - `justify-content: end` 

      ![Example of justify-content set to end](http://p0.qhimg.com/t012fdfb43be210320b.png)

    - `justify-content: center`

      ![Example of justify-content set to center](http://p0.qhimg.com/t0121f6243af228e533.png)

    - `justify-content: strech`  cambia el tamaño de los elementos de la cuadrícula para permitir que la cuadrícula llene todo el ancho del contenedor de cuadrícula

    - `justify-content: space-around` coloca una cantidad uniforme de espacio entre cada elemento de la cuadrícula, con espacios de tamaño medio en los extremos lejanos
    
      ![Example of justify-content set to space-around](http://p0.qhimg.com/t01a20181854966e956.png)
    
    - `justify-content: space-between` coloca una cantidad uniforme de espacio entre cada elemento de la cuadrícula, sin espacio en los extremos
    
      ![Example of justify-content set to space-between](http://p0.qhimg.com/t01ce2fa8742987e2d7.png)
    
    - `justify-content: space-evenly`coloca una cantidad uniforme de espacio entre cada elemento de la cuadrícula, incluidos los extremos lejanos
    
      ![Example of justify-content set to space-evenly](http://p0.qhimg.com/t01850de3364c4bbe46.png)

  

- **En Vertical(y o block)** tenemos las propiedades:
  
  - `align-content` :  alinear  toda la cuadrícula dentro del contenedor a lo largo del column axis
  
    - `align-content: start`
    
      ![Example of align-content set to start](http://p0.qhimg.com/t017f5b8278a30f5c6d.png)
    
    - `align-content: end` 
    
      ![Example of align-content set to end](http://p0.qhimg.com/t018c44b23f2d7d8bcd.png)
    
    - `align-content: center`
    
      ![Example of align-content set to center](http://p0.qhimg.com/t01e3f8dffe087bebcf.png)
    
    - `align-content: strech` cambia el tamaño de los elementos de la cuadrícula para permitir que la cuadrícula llene toda la altura del contenedor de cuadrícula
    
      ![Example of align-content set to stretch](http://p0.qhimg.com/t015b64390a99043ad4.png)
    
    - `align-content: space-around` coloca una cantidad uniforme de espacio entre cada elemento de la cuadrícula, con espacios de tamaño medio en los extremos lejanos
    
      ![Example of align-content set to space-around](http://p0.qhimg.com/t01e4088675bc8f2291.png)
    
    - `align-content: space between` coloca una cantidad uniforme de espacio entre cada elemento de la cuadrícula, sin espacio en los extremos
    
      ![Example of align-content set to space-between](http://p0.qhimg.com/t011990e6cf87af8a91.png)
    
    - `align-content : space-evenly` coloca una cantidad uniforme de espacio entre cada elemento de la cuadrícula, incluidos los extremos lejanos
    
      ![Example of align-content set to space-evenly](http://p0.qhimg.com/t0177c7695d648f9823.png)

#### **2.4.2 Items**

Estas alineaciones son para alinear el contenido de cada track. Las propiedades son muy parecidas a las de flex.

- **En horizontal(x o inline)** tenemos las propiedades:

  - **alinear elementos a lo largo del row axis**:

    - `justify-items` (todos) : **Alinea todos los ítems**  de la cuadrícula a lo largo del row axis .**(va en el container)**

      - `justify-items: start` Los items se colocan al comienzo del row axis

        ![Example of justify-items set to start](http://p0.qhimg.com/t014aac0561a2356880.png)

      - `justify-items: end` Los items se colocan al final del row axis

        ![Example of justify-items set to end](http://p0.qhimg.com/t0150250ab32231e09d.png)

      - `justify-items: center` Los items se colocan al centro del row axis

        ![Example of justify-items set to center](http://p0.qhimg.com/t0165c50666a5eb75e3.png)

      - `justify-items: stretch` Los items se estiran en todo el row axis. **Valor por defecto**

        ![Example of justify-items set to stretch](http://p0.qhimg.com/t013f7d913386d24db6.png)

        

    - `justify-self` (uno en particular)  : Alinea un item  dentro de una celda (cell) a lo largo del row axis

      - Valores 

      - start

        ![Example of justify-self set to start](http://p0.qhimg.com/t012726e6a9b31ae7b9.png)

      - end

        ![Example of justify-self set to end](http://p0.qhimg.com/t017b10ee4bdb228696.png)

      - center
    
        ![Example of justify-self set to center](http://p0.qhimg.com/t0137ce363f085b12b7.png)
      
      - stretch
      
        ![Example of justify-self set to stretch](http://p0.qhimg.com/t0129d1eb7fd5521656.png)
        
        

- **En Vertical(y o block)** tenemos las propiedades:

  - **alinear elementos a lo largo del column axis**.

    - `align-items` (todos) **Alinea todos los ítems**  de la cuadrícula a lo largo del column axis .**(va en el container)**

      - `align-items: start `Los items se colocan al comienzo del column axis

        ![Example of align-items set to start](http://p0.qhimg.com/t01ff0fa166f558197d.png)

      - `align-items: end` Los items se colocan al final del column axis

        ![Example of align-items set to end](http://p0.qhimg.com/t01db036a5039b6f137.png)

      - `align-items: center` Los items se colocan al centro del column axis

        ![Example of align-items set to center](http://p0.qhimg.com/t0169cb9db61ffbae54.png)

      - `align-items: stretch` Los items se estiran en todo el column axis.

        ![Example of align-items set to stretch](http://p0.qhimg.com/t013f7d913386d24db6.png)

    - `aling-self` (uno en particular): Alinea un item  dentro de una celda (cell) a lo largo del column axis

      - Valores:
      
      - start
      
        ![Example of align-self set to start](http://p0.qhimg.com/t0135bf5bf8c59224bb.png)
      
      - end
      
        ![Example of align-self set to end](http://p0.qhimg.com/t0138110adbf89ff364.png)
      
      - center
      
        ![Example of align-self set to center](http://p0.qhimg.com/t0176017095e3a523f2.png)
      
      - stretch
      
        ![Example of align-self set to stretch](http://p0.qhimg.com/t01808ac36d9b99d412.png)

    

  **NOTA:** También se pueden utilizar márgenes para alinear elementos.

### **2.5.  PLACEMENT**

Existe dos clases de Grid:

- Explícitos: Aquellos que definimos en la grilla, con grid-template.

- Implícitos: Aquellos que el navegador crea automáticamente cuando ya hemos llenado nuestra grilla totalmente.

- Por defecto los elemento implícitos se ajustan a su contenido. Podemos definir su tamaño con:

  - **Forman parte del grid container**
  -  `grid-auto-rows: value_size;`
  - `grid-auto-colums: value_size;`
  - `grid-auto-flow: value [dense];`   Esta propiedad especifica algo así como el eje principal.
    -   `grid-auto-flow: row | column | row dense | column dense;` 
    - Valores
      - row(predeterminado)  ----> el navegador los dibuja en fila como maquina de escribir
      - column
      - dense
    - *dense* es un valor opcional. Es utilizado para llenar huecos en la grilla en el dado caso de que haya un salto de linea por un columna que hayamos fijado.
  
  
