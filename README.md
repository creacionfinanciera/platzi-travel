# platzi-travel
Este es el repositorio de platzi-travel.


## Pasos para la instalación de tailwindcss

1. Entrar a la carpeta donde se alojara el proyecto, y los siguientes comando hacerlos dentro de la carpeta del proyecto
2. `npm init` => para iniciar nuestro proyecto, y crear el archivo package.json, damos enter a todas las preguntas.
3. `npm install -D tailwindcss postcss autoprefixer` => para instalar tailwind, y crear los modulos y el package-lock.json
4. `npx tailwindcss init -p` => para crear el archivo `tailwind.config.js` y el archivo `postcss.config.js`
5. Creamos la carpeta public, con la subcarpeta css y un archivo adentro `tailwind.css`
6. Creamos la carpeta src, con la subcarpeta css y un archivo adentro `tailwind.css`
7. Creamos un archivo `index.html` y lo ponemos dentro de la carpeta public
8. Agregamos las rutas en el archivo `tailwind.config.js`: `content: ["./public/index.html", "./src/**/*.{html,js}"]`
9. Copiamos las directivas en la documentación de la página de tailwind, y las pegamos a nuestro archivo de `tailwind.css` en la carpeta src
10. Ejecutamos el proceso de construcción con este comando: `npx tailwindcss -i ./src/css/tailwind.css -o ./public/css/tailwind.css --watch --verbose`, watch es para que muestre el proceso de construcción y verbose para que muestre si se genera algun error
11. Verificamos que se generen todas las configuraciones preeliminares en el archivo `tailwind.css` que se encuentra en la carpeta public, y que se puedan visualizar en el navegador, los primeros estilos configurados en la clase de tailwind que se hizo al principio en el html

## Directivas de Tailwind CSS

Una directiva es una instrucción que nos sirve para insertar código a nuestro archivo final de CSS:

- `@tailwind base` => Inicializa todos los elementos de nuestro HTML sin estilo 
- `@tailwind component` => Nos permite acceder a todas las clases de tailwind
- `@tailwind utilities` => Agrega todas las utilidades al proyecto y nos permite acceder a ellas

Existen muchas más directivas.

- `@tailwind screens` => Nos va a servir para modificar esos breakpoints y customizarlos como nosotros queramos
- `@apply` => La directiva tailwind nos va a servir para aplicar estilos especificamente de una manera que vamos a ver mas adelante
- `@layer` => Nos va a permitir decir justamente el bloque de código al que pertenecen los estilos
- `@variants` => Nos permite agregar componentes responsivos, pero esta orientada principalmente a agregar variantes que reaccionen a eventos como un `hover` o un `focus` o un `active`
- `@responsive` => Nos permite generar distinto tipo de responsividad en nuestras clases
- `screen()` => La función screen se usa directamente entro de la directiva `@screen`
- `theme()` => Esta función nos va a servir para acceder a los valores de configuración iniciales en tailwind

## Colores Personalizados en Tailwind

Nosotros podemos definir colores personalizados en el archivo `tailwind.config.js`, dentro de:

`theme: {`
     `colors: {`
        `primary: #5c6ac4,`
        `secondary: #ecc94b,`
     `}`
 `}`

## Medidas y breakpoints

Un breakpoint es el salto en el que cambia la pantalla de layout, por ejemplo, cuando hacemos resize en la pantalla del navegador, la podemos hacer pequeña, mediana, o totalmente grande, esto es un brakpoint y aqui es cuando nuestra pantalla cambia de layout. Podemos manipular los estilos de nuestro archivo en función al tipo de dispositivo.

Cómo mencionamos anteriormente, tailwind es `mobile first`, es decir, nosotros todo el tiempo vamos a estar trabajando tailwind con el breakpoint small, el cual es equivalente a un dispositivo mobil.

![Breakpoints](../platzi-travel/public/img/breakpoints.png)

- Breakpoint de 320px, equivalente a small y hace referencia a un dispositivo móvil
- Breakpoint de 768px, equivalente a medium y hace referencia a una tablet
- Breakpoint de 1280px, equivalente a large y hace referencia a una computadora

## Tailwind como API para la creación de un Design System

Un Design System va a ser nuestro archivo donde vamos a definir todos los estilos, tamaños, tipografías y los colores que vamos a estar utilizando dentro de nuestro proyecto.

Antes creamos una pequeña automatización, para no escribir cada que tengamos que volver a compilar nuestro archivo de tailwind:

1. Vamos al archivo `package.json`, en la sesión de "scripts"
2. Creamos la siguiente variable: `"tw:build": "tailwindcss -i ./src/css/tailwind.css -o ./public/css/tailwind.css --watch --verbose"`

Para crear el Design System, vamos al archivo `tailwind.config.js` y vamos a ver que se compone de tres principales partes:
- `purge: [],` => esto es para limpiar nuestro archivo, las veces que lo necesitemos, lo vamos a ver más adelante
- `darkMode: false,` => tambien lo vamos a integrar a nuestro proyecto más adelante
- `theme: {}` => aqui vamos a agregar todas las clases extra que vamos a ir utilizando. Dentro de `extend: {}` vamos a ir agregando nuestras imagenes, luego nuestros colores, colores para textos personalizados, las fuentes (pero antes nos traemos al HTML el código de google fonts)

## Extracción de componentes a clases para nuestra card

Podemos extraer una clase del código HTML y guardarla como una directiva, en el archivo donde se encuentran las directivas, y nombramos la clase en el HTML, de tal forma que podemos replicar esta clase para varias etiquetas, en este caso para varias cards:

.Card {
   @apply w-48 h-64 shadow-md rounded-lg
}

Cada vez que hagamos un cambio en las directivas o en los archivos base de tailwind.css, debemos correr el comando => `npm run tw:build`

## Agregando animaciones al proyecto

En algunos casos nuestras clases pueden llegar a no funcionar, y esto a veces es porque tailwind no las tiene activadas por defecto, entonces debemos proceder a comfigurarlas en el archivo `tailwind.config.js`

variants: {
    width: ["responsive", "hover", "focus"],
    extend: {},
  },






