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

   ![image-20200606154539197](img\image-20200606154539197.png)

2. `display: inline-flex`. Se comporta como un elemento de linea.

   ![image-20200606154552978](img\image-20200606154552978.png)

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

- Valores posibles
  - row (Predeterminado)

    ![image-20200606154331572](img\image-20200606154331572.png )

  - row-reverse (Horizontal, de derecha a izquierda)

    ![image-20200606154343168](img\image-20200606154343168.png)

  - column (Vertical, de arriba a abajo)
  
    ![image-20200606154358616](img\image-20200606154358616.png)
  
  - column-reverse (Vertical, de abajo a arriba)
  
    ![image-20200606154412888](img\image-20200606154412888.png)
    
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

    ![image-20200606154222298](img\image-20200606154222298.png)

  - wrap (los hijos pueden saltar de linea) //single line or multi line

    ![image-20200606154236709](img\image-20200606154236709.png)
  
  - wrap-reverse (los hijos pueden saltar de linea. Las lineas estan en el orden opuesto[el eje trasversal esta en reversa]).
  
    ![image-20200606154252605](img\image-20200606154252605.png)
    
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

    Alinea los Items en el eje principal(main axis) Sintaxis: `justify-content: value`

    Posibles Valores:

    - flex-start (Predeterminado) : Los elementos de flexbox se empujan hacia el inicio del eje principal del contenedor.

      ![image-20200606153912150](img\image-20200606153912150.png)

    - flex-end :  Los elementos de flexbox se empujan hacia el final del eje principal del contenedor.

    - center :  Los elementos de flexbox se empujan hacia el centro del eje principal del contenedor.

      ![image-20200606153954733](img\image-20200606153954733.png)

    - space-between:  Los items flex se distribuyen uniformemente sobre la línea. El espaciamiento se hace de tal manera que el espacio adyacente entre dos items es el mismo. El borde del comienzo principal y el borde del final principal se alinean al ras con el borde del primer y último item respectivamente.

      ![image-20200606154017641](img\image-20200606154017641.png)

    - space-around: Es parecido a un margen automatico. Distribuye items uniformemente. Los items flex se alinean uniformemente de tal manera que el espacio entre dos items adyacentes es el mismo. El espacio vacío anterior al primer item y posterior al último item equivale a la mitad del espacio entre dos items adyacentes.

      ![image-20200606154042728](img\image-20200606154042728.png)

    - space-evenly : Es similar al space around pero proporciona un espacio igual en lugar de medio tamaño en los bordes.

  - **Align-items**

    Alinea los Items en el eje transversal(cross axis) dentro de la linea . Sintaxis: `align-items: value`

    Define cómo se alinean los elementos de flexbox de acuerdo con el eje transversal(cross axis), *dentro de una línea de un contenedor de flexbox*. Tenemos el valor de nowrap.

    Posibles Valores:
    
    - flex-start (Predeterminado) :  : Los flexbox items se alinean al comienzo del eje transversal. cross start
    
      ![image-20200606152322447](img\image-20200606152322447.png)
    
    - flex-end : Los flexbox items se alinean al fnal del eje transversal. cross end
    
      ![image-20200606152338990](img\image-20200606152338990.png)
    
    - center :  : Los flexbox items se alinean al centro del eje transversal.
    
      ![image-20200606152357514](img\image-20200606152357514.png)
    
    - baseline : Los elementos de flexbox están alineados en la línea de base del eje transversal. Por defecto, el eje transversal es vertical . Esto significa que los elementos de flexbox se alinearán para que la línea base de su texto se alinee a lo largo de una línea horizontal.
    
      ![image-20200606152436015](img\image-20200606152436015.png)
    
    - stretch : Las elementos son estirados de modo que el tamaño transversal de sus límites sea el mismo del contenedor, manteniendo sus restricciones de anchura y altura.
    
      ![image-20200606152707778](img\image-20200606152707778.png)

- **Alineacion de Lineas**

  - Align-content

    Define cómo se alinea cada línea dentro de un contenedor flexbox . Solo se aplica si flex-wrap: wrap está presente y si hay *varias líneas de elementos de flexbox*. Alinea las lineas respecto al container . 

    Sintaxis: `align-content: value`

    Posibles valores:

    - flex-start (Predeterminado)
    
      ![image-20200606152907739](img\image-20200606152907739.png)
    
    - flex-end 
    
      ![image-20200606152926192](img\image-20200606152926192.png)
    
    - flex-center
    
      ![image-20200606152944504](C:\Users\Greis\AppData\Roaming\Typora\typora-user-images\image-20200606152944504.png)
    
    - space-between : Cada línea solo llenará el espacio que necesita. El espacio restante aparecerá entre las líneas.
    
      ![image-20200606153041343](img\image-20200606153041343.png)
    
    - space-around: Cada línea solo llenará el espacio que necesita. El espacio restante se distribuirá equitativamente alrededor de las líneas: antes de la primera línea, entre las dos y después de la última.
    
      ![image-20200606153150312](img\image-20200606153150312.png)
    
    - stretch : Cada línea se estirará para llenar el espacio restante.
    
      En este caso, el contenedor tiene una altura de 300 px. Todas las cajas tienen una altura de 50 px, excepto la segunda que tiene una altura de 100 px.
    
      La primera línea tiene 100 px de altura
      La segunda línea tiene 50px de altura.
      El espacio restante es de 150 px
      Este espacio restante se distribuye equitativamente entre las dos líneas:
    
      La primera línea tiene ahora 175px de altura
      La segunda línea tiene ahora 125px de altura
    
      ![image-20200606153618069](img\image-20200606153618069.png)
    
    - space-evenly 

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
  
    ![image-20200611105348682](img\image-20200611105348682.png)

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
  
    ![image-20200611105129899](img\image-20200611105129899.png)
  
  - Ejm: flex-basis: 80px : Puede definir valores de **píxeles** o **(r) em** . El elemento envolverá su contenido para evitar cualquier desbordamiento.
  
    ![image-20200611105141663](img\image-20200611105141663.png)

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

  ![CSS Grid Layout: A New Layout Module for the Web | WebKit](https://webkit.org/wp-content/uploads/grid-concepts.svg)

  ![image-20200617195851785](img\image-20200617195851785.png)

### **2.1 . GRID-CONTAINER**

#### **2.1.1 Display**

1. `display: grid`.(Visualmente no altera en nada al elemento, es como si aplicáramos un position:relative). Es un elemento de bloque

   ![image-20200617203044932](img\image-20200617203044932.png)

2. `display: inline-grid`. Elemento de línea

   ![image-20200617203101812](img\image-20200617203101812.png)

   


### **2.2. ELEMENTOS ABSTRACTOS (no existen en el DOM)**

- El navegador los crea para posicionar y alinear elementos.
- Son definidos en las propiedades del grid-container.

#### **2.2.1 Grid-tracks**

Son las filas y las columnas.

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

  ![image-20200617184528821](img\image-20200617184528821.png)

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

Con css-grid podemos colocar un elemento donde queramos. Esto lo hacemos especificándole la línea donde inicia y donde termina dicho elemento. Para esto utilizamos las propiedades:

```css
.element {
    grid-column-start: value;   /* Linea vertical inicial */
    grid-row-start: value;      /* Linea horizontal inicial */
    grid-column-end: value;     /* Linea vertical final */
    grid-row-end: value;        /* Linea horizontal final */
    
    /*
    Shorthands
    grid-row: value_start / value_end;
    grid-column: value_start / value_end;

    Nota: tambien podemos contar columnas o filas, utilizando las unidad 'span'. Ejemplo. una grilla 	que ocupe desde la linea 1 hasta la cuarta columna:
    grid-column: 1 / span 4; 
   
    Shorthand de grid-row-start, grid-column-start, grid-row-end, grid-column-end
    	grid-area : grid-row-start / grid-column-start / grid-row-end / grid-column-end
    /*
}
```

**NOTA1:** Los grid-items pueden ser a su vez grid-containers.

**NOTA:2** Los grid container también manejan las propiedades *justified-content* y *aling-items*.

### **2.4**.  ALINEACIÓN

#### **2.4.1 Container**

Estas propiedades las utilizamos para mover la alineación de los tracks respecto al contenedor. Las propiedades son muy parecidas a las de flex.

- En horizontal(x o inline) tenemos las propiedades:
  - justify-content : propiedad se utiliza para alinear toda la cuadrícula dentro del contenedor a lo largo del column axis

- En Vertical(y o block) tenemos las propiedades:
  - align-content : propiedad se utiliza para alinear *verticalmente* toda la cuadrícula dentro del contenedor, alinea tracks a lo largo del row axis

#### **2.4.2 Items**

Estas alineaciones son para alinear el contenido de cada track. Las propiedades son muy parecidas a las de flex.

- En horizontal(x o inline) tenemos las propiedades:
  - alinear elementos a lo largo del row axis:
    - justify-items (todos)
    - justify-self (uno en particular, se ajustan al contenido)

- En Vertical(y o block) tenemos las propiedades:

  - alinear elementos a lo largo del column axis.
    - align-items (todos)
    - aling-self (uno en particular, se ajustan al contenido)

  **NOTA:** También se pueden utilizar márgenes para alinear elementos.

### **2.5  Placement**

Existe dos clases de Grid:

- Explícitos: Aquellos que definimos en la grilla, con grid-template.
- Implícitos: Aquellos que el navegador crea automáticamente cuando ya hemos llenado nuestra grilla totalmente.

- Por defecto los elemento implícitos se ajustan a su contenido. Podemos definir su tamaño con.

  ```css
  .container {
      grid-auto-rows: value_size;
      grid-auto-colums: value_size;
  
      grid-auto-flow: value [dense]; /* Valores: row(predeterminado) | column. Esta propiedad especifica algo asi como el eje principal.
      
      *dense* es un valor opcional. Es utilizado para llenar huecos en la grilla en el dado caso de que haya un salto de linea por un columna que hayamos fijado.
      */
  }
  ```