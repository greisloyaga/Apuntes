# **JAVASCRIPT EN EL NAVEGADOR**

## **1. EL DOM**

### 1.1 EL DOM

- El modelo de objeto de documento (DOM) es una interfaz de programación para los documentos HTML y XML. 

- Toda etiqueta HTML es un objeto.

- **document** : es una variable global que representa un objeto que contiene dentro todo lo que hay en la página web.
  - document.doctype
  - document.documentElement
  - document.head
    - document.charset
    - document.title
  - document.body
    - document.links
    - document.images
    - document.getSelection()
      - toString()
  - document.scripts
  - document.styleSheets

### **1.2. NODOS**

Los nodos pueden ser etiquetas HTML, los atributos, texto,etc. son nodos.

- nodeName 

- nodeType

  https://developer.mozilla.org/es/docs/Web/API/Node/nodeType

  - 1 Elemento
  - 2 Atributo
  - 3 Texto
  - 8 Comentario

### **1.3. SELECCIONAR NODOS**

- **Con Id**

  - document.getElementById() : devuelve un único elemento, para obtener un elemento  en particular , referencia única

- **Con selectores de CSS**

  - document.querySelector() o element.querySelector()

  - document.querySelectorAll() o element.querySelectorAll()

    ```javascript
    // console.log(document.getElementById('title'))
    const title = document.getElementById('title'),
        title2 = document.querySelector('#title'),
        listItems = document.querySelectorAll('ul li'),
        secondItem = document.querySelector('ul li:nth-child(2)'),
        list = document.getElementById('list')
    title.style.background= 'yellow'
    
    console.log(title)
    console.log(title2)
    console.log(listItems)
    // console.log(listItems[1])
    console.log(secondItem)
    console.log(list.querySelectorAll('li: last-child'))
    ```

### **1.4. COLECCIONES**

- HTML Collection : solo es una lista de elementos.

- NodeList : es una lista de nodos : atributos, comentarios, texto, elementos, etc.

  ```javascript
  const nodeList = document.querySelectorAll('li')
  // querySelectorAll te devuelve una lista de nodos
  // si quieres usar el metodo map, for each,filter, each  se debe convertir un array
  //PRIMERA FORMA
  const nodeList = Array.from(document.querySelectorAll('li'))
  nodeList.map(el => {
       if(el.textContent.trim().toLocaleUpperCase() === 'OBJECT'){
           el.remove()
       }
   })
   console.log(nodeList)
  //SEGUNDA FORMA
  const nodeList = document.querySelectorAll('li')
  for (const el of nodeList) {
      if(el.textContent.trim().toLocaleUpperCase() === 'OBJECT'){
                  el.remove()
              }    
  }
  console.log(nodeList)
  ```

- Operadores con Colecciones

- childnotes

- children

### **1.5. ATRIBUTOS**

- **getAttribute()** : devuelve un atributo

- **setAttribute()**: define un atributo

- **classList**

  - **.add()**
  - **.remove()**
  - **.toggle()**

- **id**

- **value**: input de formularios

  ```javascript
  //GET
  const title = document.getElementById('title2')
  if(title){
      title.style.background = 'yellow'
  }
  console.log('Hola mundo')
  //SET
  const title = document.querySelector('h1')
  // title.setAttribute('id' ,'title')
  title.id = 'title'
  //classList.add
  title.classList.add('main-title', 'tittle-front-page')
  //classList.remove
  title.classList.remove('main-title')
  console.log(title)
  ```

### **1.6. CONTENIDO**

- El contenido es lo que esta dentro de un elemento

- Son propiedades de lectura y escritura

  - **textContent**: devuelve todo el texto
  - **innerHTML**: devuelve el HTML tal cual;
  - **outerHTML**: te devuelve todo el HTML con el elemento. Devuelve una cadena de String.

  ```javascript
  //LECTURA
  //HTML
  <h1 class="title">El <span> DOM <em>en Js</em></span></h1>
  //JAVASCRIPT
  const title = document.querySelector('h1')
  console.log(title.textContent)
  console.log(title.innerHTML)
  console.log(title.outerHTML)
  //CONSOLA
  El  DOM en Js
  El <span> DOM <em>en Js</em></span>
  <h1 class="title">El <span> DOM <em>en Js</em></span></h1>
  //ESCRITURA
  const title = document.querySelector('h1')
  title.innerHTML=`Propiedad de escritura JS`
  ```

### **1.7. CREAR ELEMENTOS**

- **document.createElement()**

- **appendChild()**

  ```javascript
  const profesor = document.createElement('p')
  profesor.textContent = `Greis Loyaga`
  profesor.classList.add('teacher') // agrega un class= 'teacher' al p
  const profesorContainer = document.getElementById('teacher')
  if (profesorContainer && profesorContainer.querySelector('span')) {
      profesorContainer.querySelector('span').appendChild(profesor)
  }
  ```

## 2. LOS EVENTOS

Es algo que ocurre en la pagina.

### **2.1. Eventos**

- onEvent

- addEventListener()

- handlers

- Objeto event

  ```javascript
  const title = document.getElementById('title')
  const button = document.querySelector('button')
  //title.addEventListener('eventName',eventHandler)
  //eventName es el tipo de evento
  //eventhandler es una funcion que se ejecuta cuando el eventName ocurra
  //se pasa como parametro el objeto, y retorna un alert seleccionando el objeto y mostrando el contenido
  const leerTextoElemento = e => alert(e.target.textContent)
  title.addEventListener ('click', e => {
      //hay que pasarle el objeto event
      leerTextoElemento(e)
  })
  button.addEventListener('click' , e =>{
      leerTextoElemento(e)
  })
  ```

### **2.2. Eventos de mouse**

- click : un solo click
- dblclick : doble click
- mouseenter : el mouse entra en el área de un elemento
- mouseleave: el mouse sale del área de un elemento
- contextmenu: capturar el click derecho, muestra el menú contextual
- mousedown: cuando haces el click y dejas presionado el click
- mouseup: cuando haces el click y sueltas el click
- mousemove: se mueve dentro de un elemento

### **2.3. Eventos de teclado**

- keydown : presionas una tecla
- keyup: sueltas una tecla
- keypress: presionas una tecla y no la sueltas

### **2.4. Eventos de formulario**

- submit: es el evento cuando el formulario se envía
- change: un campo del formulario cambia de valor
- focus : es el evento cuando haces click en un input
- blur: cada vez que sales del input 
- reset: reseteas el formulario

### **2.5. Eventos de DOM**

- DOMContentloaded

### **2.6. Eventos del navegador**

- load
- scroll : para modificar el scroll del navegador
- resize: redimensionar la pantalla del navegador

### **2.7. Eventos multimedia**

- play
- pause

### **2.8. Propagación**

- Delegación de eventos

## 3. RECORRER Y TRANSFORMAR EL DOM

### **3.1. DOM Traversing** : Recorrer el DOM

- **Hijos**
  - childNodes : devuelve todos los nodos hijos
  - children: devuelve solo elementos hijos
  - firstChild : obtiene el primer nodo hijo
  - firstElementChild : primer elemento hijo
  - lastChild : ultimo nodo hijo
  - lastElementChild : ultimo elemento hijo
  - hasChildNodes() : método que devuelve true si el elemento contiene hijos
- **Hermanos**
  - nextSibling : devuelve el nodo que sigue inmediatamente al nodo especificado
  - nextElementSibling : devuelve el elemento que sigue inmediatamente al elemento especificado
  - previousSibling: devuelve el nodo anterior del nodo especificado
  - previousElementSibling : devuelve el elemento anterior al elemento especificado
- **Padre**
  - parentNode : devuelve el nodo que sea padre
  - parentElement : devuelve el elemento padre

### **3.2. Insertar elementos**

- **appendChild()** : agregar un elemento al final
- insertBefore(new,nextNode) : el primer parámetro es el nuevo elemento, el segundo parámetro es elemento que ya existe
- insertAdjacent
  - Métodos
    - insertAdjacentElement(position,el)
    - insertAdjacentHTML(position,html)
    - insertAdjacentText(position,text)
  - Posiciones
    - beforebegin : hermano anterior
    - afterbegin : primer hijo
    - beforeend : ultimo hijo
    - afterend: hermano siguiente
- parent.replaceChild(newChild,oldChild)

### **3.3. jQueryLike**

- before() : hermano anterior
- after() : hermano siguiente
- prepend() : primer hijo
- append() : ultimo hijo
- child.replaceWith(newChild) : encuentra al hijo y reemplaza con nuevo hijo

### **3.4. Clonar y eliminar**

- **$0 : referenciar al elemento**
- cloneNode():  sacar una copia de un elemento
  - requiere un parámetro 'true' para copiar todos los hijos: cloneNode(true)
- remove() : eliminar el elemento

### **3.5. Crear elementos**

- createElement()
- createDocumentFragment() : permite guardar en memoria, y mejora rendimiento

### **3.6. Templates (HTML)**

- Permite crear plantillas
- `<template>`

### **3.7. CSSOM**

- style: manipular los estilos

- matchMedia() : evalúa una media jQuery de css

- getComputedStyle() : obtener el estilo

- getBoundingClientRect(): devuelve un objeto `ClientRect` que contiene las siguientes propiedades de la caja del elemento:

  ```javascript
  // top:    distancia al borde superior del viewport
  // left:   distancia al borde izquierdo del viewport
  // right:  distancia al borde derecho del viewport
  // bottom: distancia al borde inferior del viewport
  // width:  ancho de la caja del elemento
  // height: altura de la caja del elemento
  ```

  ![Obtener posicion de un elemento HTML con JavaScript - EDteam blog](https://api.ed.team/public-files/bloginlineimg/71409d90-579d-4861-a153-24920cd61470.png)

## 4. EL NAVEGADOR

### 4.1. El Objeto Window

Es el objeto de mas alto nivel en el navegador

- Objetos
  - console :muestra en consola información
  - navigator: da información sobre navegador
  - location : da información sobre la url
  - history : da información sobre el historial del navegador
- Métodos
  - alert(message)
  - confirm(message): modal de confirmación, devuelve un boolean
  - prompt(message) : manda un mensaje y guarda la respuesta del usuario en una variable
  - open() : abrir una nueva instancia del navegador
    - window.open ('url' , String, 'width =200, height =400')
  - close() :puedes cerrar la ventana si lo abriste con open

### 4.2. Objeto location

Muestra información sobre la URL , `location.property`

- Propiedades
  - href : url actual, se puede cambiar para cambiar la pagina actual ,`location.href`
  - host : dominio puerto
  - hostname : dominio 
  - port :puerto
  - protocol : protocolo
  - origin : protocolo + dominio
  - hash : #
  - pathname : ruta interna luego del dominio
- Métodos
  - reload()
  - assign(url)
  - replace(url) : cambia la pagina actual sin guardar en history

### 4.3. Objeto history

Contiene el historial de navegación de la pestaña en la que estas

- Propiedades
  - lenght : cantidad de elementos, incluye la pagina actual
- Métodos
  - back() : te manda atrás
  - forward() : te manda adelante
  - go(position) : -1 back, 1 forward

### 4.4. Objeto navigator

- Detectar navegador : no es buena idea
- Detectar características
  - CSS
  - JavaScript
  - Modernizr

### 4.5. Timers

Permite ejecutar acciones después de un tiempo o acciones que se ejecuta periódicamente

- setTimeout (callback,ms) : ejecuta lo que esta en el callback después se cierta cantidad de milisegundos
- setInterval (callback,ms)
  - clearInterval(interval)

### 4.6. Date

Es un objeto que trae las fechas del sistema 

- Instanciar
  - newDate()
  - newDate(year,month,day) : meses de 0 a 11
  - newDate(year,month,day,hours,minutes,seconds)
  - newDate(String)
- Métodos
  - getFullYear()
  - getMinutes()
  - getSeconds()
  - getDate() : día del mes del 1 al 30
  - getDay()
  - getMonth()
  - getTime() : milisegundos desde 1 de enero de 1970
  - getTimezoneOffset()