# Parte cero

## 0.4: Nuevo diagrama de nota
En el capítulo Cargando una página que contiene JavaScript - revisión la cadena de eventos causada al abrir la página https://studies.cs.helsinki.fi/exampleapp/notes se representa como un diagrama de secuencia

```mermaid
graph LR
B[Navegador] -- Primera vez: GET https://studies.cs.helsinki.fi/exampleapp/notes --> C[Servidor]
C[Servidor] -- Obtener--> D((Archivos HTML, CSS JavaScript))
D-- El navegador comienza a ejecutar el el codigo JS que obtiene JSON del servidor --> B[Navegador]
D((Archivos HTML, CSS JavaScript))-- Desactivar --> C
B[Navegador] -- Segunda vez: GET https://studies.cs.helsinki.fi/exampleapp/notes --> C[Servidor]
C[Servidor] -- retorna --> E((Datos tipo JSON de contenido y fecha))
E((Datos tipo JSON de contenido y fecha)) --El navegador ejecuta los llamados de las funciones y renderiza las notas --> B[Navegador]
E((Datos tipo JSON de contenido y fecha)) -- Desactivar --> C

```

## 0.5: Diagrama de aplicación de una sola página
Crea un diagrama que describa la situación en la que el usuario accede a la versión de aplicación de una sola página de la aplicación de notas en https://studies.cs.helsinki.fi/exampleapp/spa.

```mermaid 
graph LR
A[Usuario] -- Ingresa al navegador --> B[Navegador]
B[Navegador] -- Primera vez: GET https://studies.cs.helsinki.fi/exampleapp/notes --> C[Servidor]
C[Servidor] -- Obtener--> D((Archivos HTML, CSS JavaScript))
D-- El navegador comienza a ejecutar el el codigo JS que obtiene JSON del servidor --> B[Navegador]
D((Archivos HTML, CSS JavaScript))-- Desactivar --> C

B[Navegador] -- Segunda vez: GET https://studies.cs.helsinki.fi/exampleapp/notes --> C[Servidor]
C[Servidor] -- retorna --> E((Datos tipo JSON de contenido y fecha))
E((Datos tipo JSON de contenido y fecha)) --El navegador ejecuta los llamados de las funciones y renderiza las notas --> B[Navegador]
E((Datos tipo JSON de contenido y fecha)) -- Desactivar --> C

A[Usuario] -- No llena el formulario --> B[Navegador]
B[Navegador] -- Primera vez: GET- POST https://studies.cs.helsinki.fi/exampleapp/notes --> C[Servidor]
C[Servidor] -- GET data.js --> F((El servidor no recibe ningún dato del formulario))
F((El servidor no recibe ningún dato del formulario)) -- Desactivar --> C
```

## 0.6: Nueva nota en diagrama de aplicación de una sola pagina
Crea un diagrama que represente la situación en la que el usuario crea una nueva nota utilizando la versión de una sola página de la aplicación.

```mermaid
graph LR
A[Usuario] -- Ingresa al navegador --> B[Navegador]
B[Navegador] -- Primera vez: GET https://studies.cs.helsinki.fi/exampleapp/notes --> C[Servidor]
C[Servidor] -- Obtener--> D((Archivos HTML, CSS JavaScript))
D-- El navegador comienza a ejecutar el el codigo JS que obtiene JSON del servidor --> B[Navegador]
D((Archivos HTML, CSS JavaScript))-- Desactivar --> C

B[Navegador] -- Segunda vez: GET https://studies.cs.helsinki.fi/exampleapp/notes --> C[Servidor]
C[Servidor] -- Retorna --> E((Datos tipo JSON de contenido y fecha))
E((Datos tipo JSON de contenido y fecha)) --El navegador ejecuta los llamados de las funciones y renderiza las notas --> B[Navegador]
E((Datos tipo JSON de contenido y fecha)) -- Desactivar --> C

A[Usuario] -- Completa el formulario --> B[Navegador]
B[Navegador] -- Primera vez: GET- POST https://studies.cs.helsinki.fi/exampleapp/notes --> C[Servidor]
C[Servidor] -- POST --> F((Los datos JSON son recibidos y se agregan a la cola de la lista))
F((Los datos JSON son recibidos y se agregan a la cola de la lista)) --El navegador ejecuta los llamados de las funciones y renderiza las notas agregando el nuevo valor a la cola. --> B[Navegador]
B[Navegador] -- Renderiza la petición realizada y muestra al usuario --> A[Usuario]
F((Los datos JSON son recibidos y se agregan a la cola de la lista)) -- Desactivar --> C
```
