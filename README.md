# 🛠️ Proceso de Desarrollo \- Lista de Amigos

A continuación, describo el proceso de desarrollo que seguí para crear la aplicación de lista de amigos:

## 📋 Fase 1: Configuración inicial

javascript

*`// Declaración del array para almacenar los nombres de amigos`*  
`let listaAmigxs = [];`

Decisión: Elegí `let` en lugar de `const` porque la lista necesitará ser modificada (agregar/eliminar amigos).

![][image1]

### ✅ Capturar el valor del campo de entrada

Explicación de mi implementación:  
Utilicé document.querySelector() para seleccionar el elemento input con el id \#amigo y obtener su valor mediante la propiedad .value.

Recursos JavaScript utilizados:

* [`document.querySelector()`](https://developer.mozilla.org/es/docs/Web/API/Document/querySelector) \- Método que devuelve el primer elemento del documento que coincide con el grupo especificado de selectores  
  (https://developer.mozilla.org/es/docs/Web/API/Document/querySelector)  
* [`.value`](https://developer.mozilla.org/es/docs/Web/API/HTMLInputElement/value) \- Propiedad que representa el valor actual del elemento input  
  ([https://developer.mozilla.org/es/docs/Web/API/HTMLInputElement/value](https://developer.mozilla.org/es/docs/Web/API/HTMLInputElement/value))

Código implementado:

javascript  
`let amigo = document.querySelector('#amigo').value;`

### ✅ Validar la entrada

Explicación de mi implementación:  
Implementé una validación con una estructura condicional if que verifica si el valor capturado es una cadena vacía. Si se cumple esta condición, se muestra una alerta al usuario con el mensaje de error requerido y la función retorna true.

Recursos JavaScript utilizados:

* [`if...else`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/if...else) \- Sentencia que ejecuta una instrucción si una condición especificada es evaluada como verdadera.  
  [https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/if...else](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/if...else)   
* [`alert()`](https://developer.mozilla.org/es/docs/Web/API/Window/alert) \- Método que muestra un cuadro de alerta con un mensaje opcional y un botón Aceptar.  
  [https://developer.mozilla.org/es/docs/Web/API/Window/alert](https://developer.mozilla.org/es/docs/Web/API/Window/alert)   
* [`return`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/return) \- Declaración que especifica el valor a ser retornado por una función  
  [https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/return](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/return) 

Código implementado:

javascript  
`if (amigo === '') {`  
    `alert('Por favor ingresa un nombre');`  
    `return true;`  
`}`

### ✅ Actualizar el array de amigos

Explicación de mi implementación:  
Cuando la validación es exitosa (el campo no está vacío), utilizo el método .push() para agregar el nombre capturado al array listaAmigxs. Además, incluyo un console.log() para verificar en la consola que el nombre se agregó correctamente y poder hacer seguimiento del estado del array.

Recursos JavaScript utilizados:

* `array.prototype.push()`\- Método que añade uno o más elementos al final de un array y devuelve la nueva longitud del array  
  ([https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global\_Objects/Array/push](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array/push))  
* `console.log()` \- Método que muestra un mensaje en la consola web para fines de depuración  
  ([https://developer.mozilla.org/es/docs/Web/API/console/log](https://developer.mozilla.org/es/docs/Web/API/console/log))

Código implementado:

javascript  
`listaAmigxs.push(amigo);`  
`console.log(listaAmigxs);`

### ✅ Limpiar el campo de entrada

Explicación de mi implementación:  
Después de agregar exitosamente el nombre al array, utilizo document.getElementById() para seleccionar el elemento input con el id 'amigo' y establezco su propiedad value a una cadena vacía, lo que limpia el campo de texto para permitir al usuario ingresar un nuevo nombre.

Recursos JavaScript utilizados:

* `document.getElementById()` \- Método que devuelve una referencia al elemento por su ID  
  ([https://developer.mozilla.org/es/docs/Web/API/Document/getElementById](https://developer.mozilla.org/es/docs/Web/API/Document/getElementById))  
* `.value` \- Propiedad que establece o devuelve el valor del atributo value de un campo de texto  
  ([https://developer.mozilla.org/es/docs/Web/API/HTMLInputElement/value](https://developer.mozilla.org/es/docs/Web/API/HTMLInputElement/value))

Código implementado:

javascript  
`document.getElementById('amigo').value = "";`

## 🔍 Fase 2: Análisis Preliminar 

 Esta sección corresponde directamente a la EVOLUCIÓN de la Fase 2 (Función agregarAmigo()) y documenta el proceso de análisis y debugging que realicé para resolver los problemas de duplicación y lógica.

### ---

### ✅ Relación con la Tarea 1 de Fase 2: Capturar valor del input

El análisis de Fase 2 me llevó a confirmar que: La captura del input con `document.querySelector('#amigo').value` funcionaba correctamente, pero el problema estaba en cómo se llamaba la función.

### ---

### ✅ Relación con la Tarea 2 de Fase 2: Validar entrada

El análisis de Fase 2 me permitió entender que: La lógica de validación con `if (!input || input === '')` era correcta, pero los `return false` eran esenciales para cortar la ejecución.

### ---

### ✅ Relación con la Tarea 4 de Fase 2: Limpiar campo

El análisis de Fase 2 reveló que: La limpieza del campo sucedía después de las validaciones, pero se ejecutaba múltiples veces debido al problema de duplicación de eventos.

### ---

### ✅ Problema Específico Resuelto en Fase 

 Código HTML problemático original:

### `<button onclick="agregarAmigo()">Añadir</button>`

#### Código JavaScript problemático original:


 `document.getElementById('botonAgregar').addEventListener('click', function() {`

  `agregarAmigo();`

 `});`

#### Solución implementada:


 `<button type="button">Añadir</button>`

### JavaScript manteniendo solo:


 `document.getElementById('botonAgregar').addEventListener('click', agregarAmigo);`

### ---

### ✅ Conclusión de la Relación

Esta sección  documenta el PROCESO DE DEBUGGING que me llevó a las correcciones implementadas en la Fase 2\. Muestra cómo:

1. Identifiqué el problema de duplicación  

2. Analicé la lógica condicional con diagramas de flujo  

3. Comprendí el comportamiento del `return` en las funciones  

4. Implementé la solución final unificando los eventos en JavaScript  

#### Este proceso de análisis fue fundamental para llegar a la versión final funcional de la Fase 2 que ya documentamos anteriormente.

### 

## 🔍 Fase 2: Función agregarAmigo() \- Evolución Completa

### ✅ Versión Inicial \- Captura y Validación Básica

Explicación de mi implementación inicial:  
Comencé con una función básica que capturaba el valor del input y validaba si estaba vacío, mostrando una alerta en caso de error.

Código implementado:  


`function agregarAmigo(){`  
    `let amigo = document.querySelector('#amigo').value;`  
    `if (amigo === '') {`  
        `alert('Por favor ingresa un nombre');`  
        `return true;`  
    `} else {`  
        `listaAmigxs.push(amigo);`  
        `console.log(listaAmigxs);`  
        `return;`  
    `}`  
   `document.getElementById('amigo').value = "";`  
`}`

---

### 🔧 Corrección: Problema de Alcance en Limpieza de Campo

Problema detectado:  
La línea de limpieza del campo `document.getElementById('amigo').value = "";` estaba fuera del alcance de la función, causando que no se ejecutara correctamente.

Solución implementada:  
Moví la línea de limpieza dentro de la función pero fuera del bloque else, asegurando que se ejecute siempre.

Código corregido:


`function agregarAmigo(){`  
    `let amigo = document.querySelector('#amigo').value;`  
    `if (amigo === '') {`  
        `alert('Por favor ingresa un nombre');`  
        `return true;`  
    `} else {`  
        `listaAmigxs.push(amigo);`  
        `console.log(listaAmigxs);`  
	  `document.getElementById('amigo').value = "";`  
    `}`  
    `return;`  
`}`

---

### 🔧 Corrección: Validación de Nombres Duplicados

Problema detectado:  
Los nombres se podían ingresar múltiples veces, duplicando entradas en el array y perjudicando el resultado del sorteo.  

Solución implementada:  
Implementé una validación adicional con `listaAmigxs.includes(amigo)` para verificar si el nombre ya existía en el array.  

Código corregido:  


`} else if (listaAmigxs.includes(amigo)) {`  
    `alert('El nombre ya fue ingresado');`  
    `return false;`  
`}`

---

### 🔧 Corrección: Mejora en la Validación de Campo Vacío

Problema detectado:  
La validación inicial no capturaba espacios en blanco como entrada vacía.

Solución implementada:  
Agregué el método `.trim()` para eliminar espacios en blanco al inicio y final del texto.

Código corregido:


`let amigo = document.querySelector('#amigo').value.trim();`

---

### 🔧 Corrección: Lógica de Validación Mejorada

Problema detectado:  
Experimenté con diferentes operadores lógicos (\!, &&, \!==) para mejorar la validación.

Solución implementada:  
Probé varias aproximaciones hasta encontrar la validación más efectiva para campo vacío.

Código de experimentación:


*`// Versión con operador OR`*  
`if (!amigo | amigo === '') {`

*`// Versión con operador AND`*    
`if (amigo === '' && document.querySelector('#amigo').value !== '') {`

---

### ✅ Versión completa

Explicación de mi implementación final:  
Después de varias iteraciones, llegué a una versión robusta que incluye todas las validaciones necesarias y maneja correctamente los edge cases.

Código final implementado:


`let listaAmigxs = [];`  
`function agregarAmigo(){`  
    `let amigo = document.querySelector('#amigo').value.trim();`  
    `if (!amigo || amigo === '') {`  
        `alert('Por favor ingresa un nombre');`  
        `return true;`  
    `} else if (listaAmigxs.includes(amigo)) {`  
        `alert('El nombre ya fue ingresado');`  
        `return false;`  
    `} else {`  
        `listaAmigxs.push(amigo);`  
        `console.log(listaAmigxs);`  
	`document.querySelector('#amigo').value =''`  
    `}`  
`}`  
`document.getElementById('botonAgregar').addEventListener('click', agregarAmigo);`

Recursos JavaScript utilizados en todas las iteraciones:

* document.querySelector() \- Método que devuelve el primer elemento que coincide con el selector  
  ([https://developer.mozilla.org/es/docs/Web/API/Document/querySelector](https://developer.mozilla.org/es/docs/Web/API/Document/querySelector))  
* .value \- Propiedad que representa el valor de un input  
  ([https://developer.mozilla.org/es/docs/Web/API/HTMLInputElement/value](https://developer.mozilla.org/es/docs/Web/API/HTMLInputElement/value))  
* .trim() \- Método que elimina espacios en blanco de ambos extremos de una cadena  
  ([https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global\_Objects/String/trim](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/String/trim))  
* Array.prototype.push() \- Método para agregar elementos a un array  
  ([https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global\_Objects/Array/push](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array/push))  
* Array.prototype.includes() \- Método que determina si un array incluye un elemento  
  ([https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global\_Objects/Array/includes](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array/includes))  
* addEventListener() \- Método para registrar event handlers  
  ([https://developer.mozilla.org/es/docs/Web/API/EventTarget/addEventListener](https://developer.mozilla.org/es/docs/Web/API/EventTarget/addEventListener))

## 

## 🔍 Fase 2: Función agregarAmigo() \- Versión Modular

### ✅ Reorganización Modular del Código

Explicación de mi implementación:  
Decidí reorganizar el código en funciones modulares específicas por tarea para mejorar la legibilidad, mantenibilidad y seguir el principio de responsabilidad única. Cada función se encarga de una tarea específica.

---

### ✅ Función obtenerNombre()

Explicación de mi implementación:  
Creé una función dedicada exclusivamente a obtener y limpiar el valor del input, utilizando `.trim()` para eliminar espacios en blanco innecesarios.

Recursos JavaScript utilizados:

* document.getElementById() \- Método que devuelve una referencia al elemento por su ID  
  ([https://developer.mozilla.org/es/docs/Web/API/Document/getElementById](https://developer.mozilla.org/es/docs/Web/API/Document/getElementById))  
* .value \- Propiedad que representa el valor actual del elemento input  
  ([https://developer.mozilla.org/es/docs/Web/API/HTMLInputElement/value](https://developer.mozilla.org/es/docs/Web/API/HTMLInputElement/value))  
* .trim() \- Método que elimina espacios en blanco de ambos extremos de una cadena  
  ([https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global\_Objects/String/trim](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/String/trim))

Código implementado:


`function obtenerNombre() {`  
    `let input = document.getElementById('amigo').value.trim();`  
    `console.log(input);`  
    `return input;`  
`}`

---

### ✅ Función verificarAmigo()

Explicación de mi implementación:  
Implementé una función separada para todas las validaciones, que verifica tanto campos vacíos como nombres duplicados, retornando true o false según sea válido.

Recursos JavaScript utilizados:

* Array.prototype.includes() \- Método que determina si un array incluye un determinado elemento  
  ([https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global\_Objects/Array/includes](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array/includes))  
* Operador lógico OR (||) \- Operador que devuelve true si alguno de los operandos es true  
  ([https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/Logical\_OR](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/Logical_OR))  
* alert() \- Método que muestra un cuadro de alerta con un mensaje  
  ([https://developer.mozilla.org/es/docs/Web/API/Window/alert](https://developer.mozilla.org/es/docs/Web/API/Window/alert))

Código implementado:


`function verificarAmigo(input) {`  
    `if (!input || input === '') {`  
        `alert('Por favor ingresa un nombre');`  
        `return false;`  
    `} else if (listaAmigxs.includes(input)) {`  
        `alert('Este nombre fue ingresado, por favor ingresa otro');`  
        `return false;`  
    `}`  
    `return true;`  
`}`

---

### ✅ Función limpiarCampo()

Explicación de mi implementación:  
Creé una función específica para limpiar el campo de entrada, separando esta responsabilidad de la lógica principal de agregar amigos.

Recursos JavaScript utilizados:

* document.getElementById() \- Método que devuelve una referencia al elemento por su ID  
  ([https://developer.mozilla.org/es/docs/Web/API/Document/getElementById](https://developer.mozilla.org/es/docs/Web/API/Document/getElementById))  
* .value \- Propiedad que establece o devuelve el valor de un campo de texto  
  ([https://developer.mozilla.org/es/docs/Web/API/HTMLInputElement/value](https://developer.mozilla.org/es/docs/Web/API/HTMLInputElement/value))

Código implementado:


`function limpiarCampo() {`  
    `document.getElementById('amigo').value = "";`  
    `return;`  
`}`

---

### ✅ Función Principal agregarAmigo()

Explicación de mi implementación:  
La función principal ahora coordina las funciones modularizadas, llamándolas en secuencia y manteniendo un flujo claro y organizado.

Código implementado:

`function agregarAmigo() {`  
    `let nombre = obtenerNombre();`  
    `if (verificarAmigo(nombre)) {`   
        `listaAmigxs.push(nombre);`  
        `console.log(listaAmigxs);`  
        `limpiarCampo();`  
    `}`  
`}`

---

### ✅ Event Listener Modular

Explicación de mi implementación:  
Mantuve el event listener pero usando una función anónima que llama a la función principal, manteniendo la separación de concerns.

Código implementado:


`document.getElementById('botonAgregar').addEventListener('click', function() {`  
    `agregarAmigo();`  
`});`

**Esta reorganización modular demuestra mi evolución en el diseño de código y la aplicación de principios de clean code para crear un software más mantenible y escalable.**

## 

## ---

## 🔍 Fase 2: Función agregarAmigo() \- Versión Modular Mejorada

### ✅ Por qué reorganicé el código

Explicación de los cambios:  
El código anterior tenía problemas de lógica que hacían que no funcionara correctamente. Decidí separar cada tarea en funciones específicas para poder enfocarme en resolver una cosa a la vez y que fuera más fácil entender y corregir el flujo del programa.

---

### ✅ Función obtenerNombre() \- Para capturar el nombre

Explicación de mi implementación:  
Esta función se encarga solo de obtener el texto que el usuario escribe en el campo y limpiarlo quitando espacios de más al principio y final.

Código implementado:


`function obtenerNombre() {`  
    `let input = document.getElementById('amigo').value.trim();`  
    `console.log(input);`  
    `return input;`  
`}`

*\[VIDEO: Mostrar funcionamiento del trim() quitando espacios\]*

---

### ✅ Función verificarAmigo() \- Para validar el nombre

Explicación de mi implementación:  
Esta es la parte más importante que corregí. Ahora verifica dos cosas:

1. Que el campo no esté vacío (muestra alerta y retorna false)  
2. Que el nombre no esté duplicado (muestra alerta y retorna false)  
   Solo retorna true si el nombre es válido y no está repetido.

Código implementado:


`function verificarAmigo(input) {`  
    `if (!input || input === '') {`  
        `alert('Por favor ingresa un nombre');`  
        `return false;`  
    `} else if (listaAmigxs.includes(input)) {`  
        `alert('Este nombre fue ingresado, por favor ingresa otro');`  
        `return false;`  
    `}`  
    `return true;`  
`}`

*\[VIDEO: Mostrar las alertas de validación funcionando\]*

---

### ✅ Función limpiarCampo() \- Para borrar el input

Explicación de mi implementación:  
Esta función simplemente limpia el campo de texto después de agregar un nombre, para que el usuario pueda escribir uno nuevo.

Código implementado:


`function limpiarCampo() {`  
    `document.getElementById('amigo').value = "";`  
    `return;`  
`}`

*\[VIDEO: Mostrar cómo se limpia el campo después de agregar\]*

---

### ✅ Función Principal agregarAmigo() \- Coordina todo

Explicación de mi implementación:  
La función principal ahora llama a las otras funciones en orden:

1. Obtiene el nombre  
2. Verifica si es válido  
3. Si es válido, lo agrega a la lista y limpia el campo  
4. Si no es válido, muestra la alerta y no hace nada más

Código implementado:


`function agregarAmigo() {`  
    `let nombre = obtenerNombre();`  
    `if (verificarAmigo(nombre)) {`   
        `listaAmigxs.push(nombre);`  
        `console.log(listaAmigxs);`  
        `limpiarCampo();`  
    `}`  
`}`

*\[VIDEO: Mostrar el flujo completo funcionando\]*

---

### ✅ Cómo se activa la función

Explicación de mi implementación:  
El botón de agregar ahora llama a la función principal cuando se hace clic en él.

Código implementado:


`document.getElementById('botonAgregar').addEventListener('click', function() {`  
    `agregarAmigo();`  
`});`

La principal mejora fue en la lógica de verificación: ahora los return false hacen que la función se detenga inmediatamente cuando hay un error, evitando que se ejecuten las demás partes del código cuando no deberían.

*\[VIDEO: Comparación antes/después mostrando cómo se solucionaron los problemas\]*

**Estos cambios hicieron que el programa funcione correctamente y sea más fácil de entender y mantener.**

## 🔍 Fase 4: Análisis Preliminar \- Diagramas de Flujo y Estructura

### 📊 Diagrama 1: Comparación HTML vs JavaScript

Explicación del concepto:  
Entendí la diferencia fundamental entre la estructura HTML estática y la manipulación dinámica con JavaScript:


`HTML (Estructura Estática)`  
`=======================`  
`<ul id="listaAmigos"></ul> ← Contenedor vacío preparado`

`JavaScript (Comportamiento Dinámico)`    
`===========================`  
`1. Seleccionar el contenedor`  
`2. Limpiar contenido existente`  
`3. Recorrer array listaAmigxs`  
`4. Crear elementos <li> dinámicamente`  
`5. Agregar al contenedor HTML`

Key Insight: El HTML provee el "lugar" donde mostrar los datos, mientras que JavaScript provee los "datos" y la "lógica" para mostrarlos.

---

### 📊 Diagrama 2: Flujo de Datos entre Array y HTML

Explicación del flujo:  
Desarrollé este flujo para entender cómo los datos viajan entre el array y la visualización:


`[Array listaAmigxs] ← Almacenamiento principal`  
    `|`  
    `v`  
`[Función mostrarAmigxs()] ← Procesamiento`  
    `|`   
    `v`  
`[Elementos <li> creados] ← Transformación`  
    `|`  
    `v`  
`[HTML <ul> actualizado] ← Visualización`

Key Insight: El array es la "fuente de verdad" \- el HTML solo refleja su estado actual.

---

### 📊 Diagrama 3: Comportamiento de appendChild()

Explicación del proceso:  
Analicé cómo funciona appendChild() paso a paso:


`[document.createElement('li')] → Crea nodo en memoria`  
    `|`  
    `v`  
`[li.textContent = nombre] → Agrega contenido`  
    `|`  
    `v`  
`[ul.appendChild(li)] → Conecta al DOM`  
    `|`  
    `v`  
`[Visible en página] ← Se renderiza`

Key Insight: Los elementos se crean primero en memoria y luego se conectan al DOM.

---

### 📊 Diagrama 4: Ciclo Completo de Actualización

Explicación del flujo completo:  
Este diagrama muestra el ciclo completo desde que se agrega un nombre hasta que se muestra:


`[Usuario agrega nombre] → [Validación] → [Si válido:]`  
    `|`  
    `v`  
`[Agrega a listaAmigxs] → [Array actualizado]`  
    `|`  
    `v`  
`[Limpiar HTML] → [Preparar para nuevos datos]`  
    `|`  
    `v`  
`[Recorrer array] → [Por cada nombre:]`  
    `|`  
    `v`  
`[Crear <li>] → [Configurar texto] → [Agregar al <ul>]`  
    `|`  
    `v`  
`[HTML actualizado] ← [Usuario ve cambios]`

Key Insight: La actualización es atómica \- siempre se muestra el estado completo del array.

---

### 📊 Diagrama 5: Manejo de Nodos DOM

Explicación de la estructura de nodos:  
Entendí la jerarquía de nodos que se crea:


`Document`  
    `|`  
    `v`  
`<ul id="listaAmigos"> ← Nodo elemento`  
    `|`  
    `v`  
`<li> ← Nodo elemento (creado dinámicamente)`  
    `|`  
    `v`  
`"Nombre" ← Nodo texto (contenido)`

Key Insight: Cada elemento y texto son nodos independientes en el árbol DOM.

---

### 🎯 Decisiones de Implementación Basadas en el Análisis

1\. Elección de createElement sobre innerHTML:

* ✅ Más control sobre los nodos individuales  
* ✅ Mejor performance para actualizaciones frecuentes  
* ✅ Código más mantenible y debuggeable

2\. Limpieza sistemática del HTML:

* ✅ Previene duplicados  
* ✅ Garantiza consistencia entre array y visualización  
* ✅ Simplifica la lógica de actualización

3\. Uso de bucle for clásico:

* ✅ Mayor control sobre el índice y proceso  
* ✅ Mejor para entender los fundamentos  
* ✅ Fácil transición a otros métodos después

4\. Integración automática:

* ✅ La lista se actualiza automáticamente  
* ✅ No requiere intervención manual del usuario  
* ✅ Experiencia de usuario más fluida

---

### 🔍 Insights Clave del Análisis

Separación de preocupaciones:

* HTML: Estructura y contenedores  
* JavaScript: Datos y comportamiento  
* CSS: Presentación y estilos

Flujo de datos unidireccional:


`Array → Procesamiento → Transformación → Visualización`

Importancia de la limpieza:

* Elimina estado anterior  
* Previene memory leaks  
* Garantiza consistencia

Ventajas del enfoque de nodos:

* Manipulación precisa del DOM  
* Mejor performance que innerHTML  
* Código más expresivo y mantenible

*\[VIDEO: Mostrar el proceso de análisis y cómo se tradujo en la implementación final\]*

## 🔍 Fase 4: Función mostrarAmigxs() \- Implementación Final

### ✅ Análisis y Decisiones Previas

Explicación del proceso:  
Después de un extenso análisis de flujos y consideraciones técnicas, implementé la función `mostrarAmigxs()` siguiendo estos principios:

1. Separación de responsabilidades: Función dedicada solo a mostrar la lista  
2. Limpieza preventiva: Siempre limpiar el HTML antes de mostrar  
3. Uso de nodos DOM: Trabajar con `createElement` en lugar de innerHTML para mejor control  
4. Integración con existentes: Llamar esta función después de agregar amigos

---

### ✅ Tarea 1: Seleccionar el elemento contenedor

Explicación de mi implementación:  
Utilicé `document.getElementById()` para seleccionar el elemento `<ul>` donde se mostrarán los nombres, guardando la referencia en una variable para usarla throughout la función.

Recursos JavaScript utilizados:

* document.getElementById() \- Método que devuelve una referencia al elemento por su ID  
  ([https://developer.mozilla.org/es/docs/Web/API/Document/getElementById](https://developer.mozilla.org/es/docs/Web/API/Document/getElementById))

Código implementado:


`let lista = document.getElementById('listaAmigos');`

---

### ✅ Tarea 2: Limpiar la lista existente

Explicación de mi implementación:  
Establecí `innerHTML = ''` para limpiar completamente el contenido del `<ul>` antes de agregar nuevos elementos, evitando duplicados y asegurando que la lista refleje siempre el estado actual del array.

Recursos JavaScript utilizados:

* Element.innerHTML \- Propiedad que establece o obtiene la sintaxis HTML describing the descendants of the element  
  ([https://developer.mozilla.org/es/docs/Web/API/Element/innerHTML](https://developer.mozilla.org/es/docs/Web/API/Element/innerHTML))

Código implementado:


`lista.innerHTML = '';`

---

### ✅ Tarea 3: Recorrer el array con bucle for

Explicación de mi implementación:  
Elegí un bucle `for` clásico para recorrer el array `listaAmigxs`, accediendo a cada elemento por su índice y procesándolo individualmente.

Recursos JavaScript utilizados:

* for statement \- Crea un bucle que consiste en tres expresiones opcionales  
  ([https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/for](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/for))  
* Array.length \- Propiedad que devuelve el número de elementos del array  
  ([https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global\_Objects/Array/length](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array/length))

Código implementado:


`for (let i = 0; i < listaAmigxs.length; i++) {`  
    `// Procesar cada elemento`  
`}`

---

### ✅ Tarea 4: Crear elementos li para cada nombre

Explicación de mi implementación:  
Dentro del bucle, usé `document.createElement()` para crear un nuevo elemento `<li>` para cada nombre y `textContent` para asignarle el texto correspondiente.

Recursos JavaScript utilizados:

* document.createElement() \- Crea el elemento HTML especificado por su tagName  
  ([https://developer.mozilla.org/es/docs/Web/API/Document/createElement](https://developer.mozilla.org/es/docs/Web/API/Document/createElement))  
* Node.textContent \- Propiedad que representa el contenido textual de un nodo y sus descendientes  
  ([https://developer.mozilla.org/es/docs/Web/API/Node/textContent](https://developer.mozilla.org/es/docs/Web/API/Node/textContent))

Código implementado:


`let li = document.createElement('li');`  
`li.textContent = listaAmigxs[i];`

---

### ✅ Tarea 5: Agregar elementos al DOM

Explicación de mi implementación:  
Utilicé `appendChild()` para agregar cada elemento `<li>` creado al elemento `<ul>` principal, haciendo que sean visibles en la página.

Recursos JavaScript utilizados:

* Node.appendChild() \- Añade un nodo al final de la lista de hijos de un nodo padre especificado  
  ([https://developer.mozilla.org/es/docs/Web/API/Node/appendChild](https://developer.mozilla.org/es/docs/Web/API/Node/appendChild))

Código implementado:


`lista.appendChild(li);`

---

### ✅ Función Completa mostrarAmigxs()

Código final implementado:


`function mostrarAmigxs() {`  
    `let lista = document.getElementById('listaAmigos');`  
    `listaUl.innerHTML = '';`  
      
    `for (let i = 0; i < listaAmigxs.length; i++) {`  
        `let li = document.createElement('li');`  
        `li.textContent = listaAmigxs[i];`  
        `listaUl.appendChild(li);`  
    `}`  
`}`

---

### ✅ Integración con agregarAmigo()

Explicación de mi implementación:  
Modifiqué la función `agregarAmigo()` para llamar a `mostrarAmigxs()` después de agregar un nombre válido al array, asegurando que la lista se actualice automáticamente.

Código implementado:


`function agregarAmigo() {`  
    `let nombre = obtenerNombre();`  
    `if (verificarAmigo(nombre)) {`   
        `listaAmigxs.push(nombre);`  
        `console.log(listaAmigxs);`  
        `limpiarCampo();`  
        `mostrarAmigxs(); // ← Nueva línea agregada`  
    `}`  
`}`

---

### 🎯 Flujo Completo Implementado


`[Agregar nombre] → [Validar] → [Si válido: agregar a array] → [Limpiar input] → [Mostrar lista actualizada]`

Resultado: La lista HTML ahora se actualiza automáticamente cada vez que se agrega un nuevo nombre válido, reflejando siempre el estado actual del array `listaAmigxs`.

*\[VIDEO: Mostrar el funcionamiento completo con actualización automática de la lista\]*

## 🔍 Fase 3: Función sortearAmigos() \- Implementación Final

### ✅ Análisis y Decisiones Previas

Explicación del proceso:  
Después de analizar los requisitos y experimentar con diferentes enfoques, implementé la función de sorteo considerando:

1. Validación robusta: Verificar que el array no esté vacío antes de sortear  
2. Aleatoriedad real: Uso correcto de Math.random() y Math.floor()  
3. Manejo de errores: Feedback claro al usuario cuando no hay amigos  
4. Visualización adecuada: Mostrar el resultado en el HTML de forma clara

---

### ✅ Tarea 1: Validar que haya amigos disponibles

Explicación de mi implementación:  
Implementé una validación que verifica si el array `listaAmigxs` está vacío usando `length === 0`, mostrando una alerta y saliendo de la función inmediatamente si no hay elementos.

Recursos JavaScript utilizados:

* Array.length \- Propiedad que devuelve el número de elementos en un array  
  ([https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global\_Objects/Array/length](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array/length))  
* alert() \- Método que muestra un cuadro de alerta con un mensaje  
  ([https://developer.mozilla.org/es/docs/Web/API/Window/alert](https://developer.mozilla.org/es/docs/Web/API/Window/alert))  
* return \- Declaración que termina la ejecución de la función  
  ([https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/return](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/return))

Código implementado:


`if (listaAmigxs.length === 0) {`  
    `alert('No agregaste amigos para sortear');`  
    `return;`  
`}`

---

### ✅ Tarea 2: Generar un índice aleatorio

Explicación de mi implementación:  
Utilicé `Math.random()` para generar un número decimal aleatorio entre 0 y 1, lo multipliqué por la longitud del array, y usé `Math.floor()` para redondear hacia abajo y obtener un índice válido.

Recursos JavaScript utilizados:

* Math.random() \- Función que devuelve un número pseudo-aleatorio entre 0 y 1  
  ([https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global\_Objects/Math/random](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Math/random))  
* Math.floor() \- Función que devuelve el máximo entero menor o igual a un número  
  ([https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global\_Objects/Math/floor](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Math/floor))

Código implementado:


`let indice = Math.floor(Math.random() * listaAmigxs.length);`

---

### ✅ Tarea 3: Obtener el nombre sorteado

Explicación de mi implementación:  
Accedí al array `listaAmigxs` usando el índice aleatorio generado para obtener el nombre correspondiente.

Recursos JavaScript utilizados:

* Array index access \- Acceso a elementos de array mediante índice  
  ([https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global\_Objects/Array\#acceder\_a\_un\_elemento\_de\_array\_por\_su\_%C3%ADndice](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array#acceder_a_un_elemento_de_array_por_su_%25C3%25ADndice))

Código implementado:


`let amigoSorteado = listaAmigxs[indice];`

---

### ✅ Tarea 4: Mostrar el resultado en HTML

Explicación de mi implementación:  
Seleccioné el elemento del DOM con id 'resultado', limpié su contenido previo y establecí el textContent con el mensaje del amigo sorteado usando template literals.

Recursos JavaScript utilizados:

* document.getElementById() \- Método que devuelve una referencia al elemento por su ID  
  ([https://developer.mozilla.org/es/docs/Web/API/Document/getElementById](https://developer.mozilla.org/es/docs/Web/API/Document/getElementById))  
* Element.innerHTML \- Propiedad para establecer contenido HTML  
  ([https://developer.mozilla.org/es/docs/Web/API/Element/innerHTML](https://developer.mozilla.org/es/docs/Web/API/Element/innerHTML))  
* Node.textContent \- Propiedad para establecer contenido textual  
  ([https://developer.mozilla.org/es/docs/Web/API/Node/textContent](https://developer.mozilla.org/es/docs/Web/API/Node/textContent))  
* Template literals \- Cadena de texto que permite expresiones embebidas  
  ([https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Template\_literals](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Template_literals))

Código implementado:


`let resultado = document.getElementById('resultado');`  
`resultado.innerHTML = '';`  
``resultado.textContent = `tu amigo sorteado es ${amigoSorteado}`;``

---

### ✅ Función Completa sortearAmigos()

Código final implementado:


`function sortearAmigos(){`  
    `if (listaAmigxs.length === 0) {`  
        `alert('No agregaste amigos para sortear');`  
        `return;`  
    `}`  
      
    `let indice = Math.floor(Math.random() * listaAmigxs.length);`  
    `let amigoSorteado = listaAmigxs[indice];`  
      
    `let resultado = document.getElementById('resultado');`  
    `resultado.innerHTML = '';`  
    ``resultado.textContent = `tu amigo sorteado es ${amigoSorteado}`;``  
`}`

---

### ✅ Integración con HTML y Event Listener

Explicación de mi implementación:  
Modifiqué el HTML para usar un event listener en JavaScript en lugar de onclick, manteniendo la separación entre estructura y comportamiento.

HTML implementado:


`<button id="botonSortear" class="button-draw" type="button" aria-label="Sortear amigo secreto">`  
    `<img src="assets/play_circle_outline.png" alt="Ícono para sortear">`  
    `Sortear amigo`  
`</button>`

JavaScript para el event listener:


`document.getElementById('botonSortear').addEventListener('click', sortearAmigos);`

---

### 🎯 Flujo Completo Implementado


`[Click en botón Sortear] → [Validar array no vacío] → [Generar índice aleatorio]`   
    `→ [Obtener nombre del array] → [Mostrar resultado en HTML]`

Problemas resueltos:

* ✅ Error de null con getElementById: Solucionado agregando id al botón  
* ✅ Validación correcta de array vacío: Usando length \=== 0 en lugar de comparación con string  
* ✅ Separación HTML/JavaScript: Eliminando onclick del HTML  
* ✅ Manejo de errores: Alert claro cuando no hay amigos para sortear

Resultado: La función ahora sortea correctamente un amigo aleatorio y muestra el resultado en la página, con validaciones robustas y manejo adecuado de errores.

*\[VIDEO: Mostrar el funcionamiento del sorteo con diferentes casos\]*

## 🎉 Conclusión del Proyecto

Este proyecto representó mi primer desarrollo completo en JavaScript, donde logré implementar exitosamente las cuatro funcionalidades principales solicitadas:

### ✅ Lo que aprendí y logré

* Manejo del DOM: Aprendí a seleccionar, crear y manipular elementos HTML dinámicamente  
* Arrays y sus métodos: Domine el uso de arrays para almacenar y gestionar datos  
* Event handling: Implementé event listeners para hacer la aplicación interactiva  
* Validaciones: Desarrollé lógica robusta para manejar entradas del usuario  
* Debugging: Superé problemas técnicos como la duplicación de eventos y null references

### 🔄 Proceso de aprendizaje

El desarrollo me permitió entender la importancia de:

* Planificar con diagramas de flujo antes de codificar  
* Separar responsabilidades en funciones modulares  
* Validar exhaustivamente las entradas del usuario  
* Mantener consistencia entre el estado de los datos y su visualización

### 🚀 Próximos pasos

Este proyecto sienta las bases para continuar mi journey en programación y análisis de datos, demostrando que puedo traducir requerimientos en funcionalidades técnicas.

---

Desarrollado con dedicación como parte del programa Oracle \+ Alura  
*\[Tu nombre\]* \- *\[Fecha de entrega\]*

