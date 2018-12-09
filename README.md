<img src="./readme-assets/title.png" alt="readme-title" width="100%"/>

## ¿ Qué haremos ?

Haremos una Landing Page tanto para Web como para Mobile usando SASS y BEM.

## ¿ Qué debemos hacer para comenzar ?

1. Debes tener instalado Git en tu computador.
2. Clonar este repositorio. Nos puedes preguntar si tienes dudas de cómo hacer este paso.
3. Abrir tu editor de código favorito: Visual Studio Code, Atom, Webstorm...
4. Abrir este repositorio en tu editor de código.
5. Escuchar atentamente las indicaciones posteriores. Haremos todo en conjunto, así que debemos esperar a que todos estemos en este paso.

# Comencemos con nuestra Landing Page !

1. [Introducción a SASS](#1-introducción-a-sass-syntactically-awesome-stylesheets)
2. [Introducción a BEM](#2-introducción-a-bem-block-element-modifier)
3. [Después de clonar el repositorio...](#3-después-de-clonar-el-repositorio)
4. [Conozcamos la estructura de nuestra Landing Page](#4-conozcamos-la-estructura-de-nuestra-landing-page)
5. [Definición de elementos](#5-definición-de-elementos)
6. [Instalación de SASS](#6-instalación-de-sass)
7. [Variables: Paleta de colores y fuentes](#7-variables-paleta-de-colores-y-fuentes)
8. [Header](#8-header)
9. [Main Section](#9-main-section)
13. [Footer](#13-footer)

## 1. Introducción a SASS (Syntactically Awesome StyleSheets)

SASS es un preprocesador de CSS y nos permite escribir CSS con unas pequeñas modificaciones: podemos hacer variables, extender estilos de otras clases, hacer anidamientos, utilizar condicionales, entre otros. 

Aquí te compartimos algunos recursos:

* Documentación oficial: https://sass-lang.com/
* Cheatsheet: https://devhints.io/sass

## 2. Introducción a BEM (Block, Element, Modifier)

* Documentación: https://en.bem.info/methodology/quick-start/

## 3. Después de clonar el repositorio...

Después de clonar el repositorio encontrarás dos carpetas: inicial y final. Tú comenzarás a escribir código en el `index.html` que dejamos para ti en la carpeta inicial. Y porsupuesto, en la carpeta final está el resultado al que debemos llegar.

## 4. Conozcamos la estructura de nuestra Landing Page

Aquí te presentamos la estructura de nuestra Landing Page. Para este caso, escogimos una página de animales pero tú puedes hacerla del tema que quieras: motos, carros, maquillaje, ropa, fitness... e inclusive, tu propia página web. 

* ## Landing Page | Diseño Web

> Mockup Link: https://goo.gl/Qbngyz

<img src="./readme-assets/landing-web.gif" alt="Landing Page Web" width="500" />

* ## Landing Page | Diseño Móvil

> Mockup Link: https://goo.gl/gGkwDq

<img src="./readme-assets/landing-mobile.gif" alt="Landing Page Mobile" width="500" />

## 5. Definición de elementos

Para comenzar a maquetar nuestra Landing Page es importante poder reconocer los elementos que allí se encuentran. Es decir, si tiene navbar, header, secciones, imágenes, footer, etc.

* ## Definición de elementos: Landing Page | Diseño Web

* ## Definición de elementos: Landing Page | Diseño Móvil

## 6. Instalación de SASS 

Lo primero que debes saber es que *no* puedes insertar directamente un archivo `.scss` en un archivo `.html`.

¿Por qué? 

Porque SASS al ser un preprocesador de CSS3 y no es soportado en los navegadores web.

Entonces los pasos a seguir son: 

* Instalación de SASS en tu computador con npm: `npm install -g sass`
> Nota: Puedes mirar otras opciones de instalación aquí: https://sass-lang.com/install

* Escribir en tu consola: `sass --watch tu-ruta/sass-workshop/initial/styles.scss tu-ruta/sass-workshop/initial/styles/index.css`
> Nota: "tu-ruta" es el lugar en tu computador en donde clonaste el repositorio. Un ejemplo puede ser: /Users/PepitaPerez/Documentos/... 

* Notarás que se crea un archivo `styles.css.map` 

## 7. Variables: Paleta de colores y fuentes

Las variables en SASS son un camino para almacenar información y poder reutilizarla. 

En nuetro caso, la paleta de colores es: 

* Verde: #99DDCC
* Rosado: #FA91A7
* Amarillo: #D9E540
* Blanco: #FFF

y, la fuente que usaremos se llama: Roboto. 

> Nota: Recuerda que puedes escoger los colores y las fuentes que desees. 

Lo que haremos para definir estas *variables* en nuestro archivo `styles.scss` es escribir lo siguiente:

```
$green: #99DDCC;
$pink: #FA91A7;
$yellow: #D9E540;
$white: #FFF;
$font-arial: arial;
```

## 8. Header 

* Imagen del mockup:

<img src="./readme-assets/header.png" alt="Navbar" />

Podemos notar que nuestro Header debe ocupar todo el ancho de nuestra página (tanto en web como en mobile), un largo de 80px y que además tiene un texto en mayúscula y centrado. Así que:

* En el archivo HTML escribiremos lo siguiente:

```
<nav class="header">Medellín CSS</nav>
```

* En el archivo SCSS escribiremos lo siguiente:

```
.header {
  background-color: $green;
  color: $white;
  width: 100%;
  height: 80px;
  text-transform: uppercase;
  font-family: $font-arial;
  font-size: 18px;
  font-weight: bold;
  letter-spacing: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
}
```

Puedes notar que tenemos: `font-family`, `font-size`, `font-weight` y con SASS podemos escribir eso así:

```
font: {
    family: $font-arial;
    size: 18px;
    weight: bold;
}
```

Así que nuestra clase `.header` quedaría:

```
.header {
  background-color: $green;
  color: $white;
  width: 100%;
  height: 80px;
  text-transform: uppercase;
  letter-spacing: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
  font: {
    family: $font-arial;
    size: 18px;
    weight: bold;
  }
}
```

Sin embargo, si pensamos a futuro vamos a notar que necesitaremos centrar elementos usando `display: flex`, por lo que sería útil hacer una clase que centre elementos y así poderla reutilizar más adelante. Por lo tanto, crearemos una clase llamada `.center` con lo siguiente:

```
.center {
  display: flex;
  align-items: center;
  justify-content: center;
}
```

Y, en nuestra clase `.header` vamos a heredar de `.center` usando `@extend` así:

```
.header {
  @extend .center;
  background-color: $green;
  color: $white;
  width: 100%;
  height: 80px;
  text-transform: uppercase;
  letter-spacing: 5px;
  font: {
    family: $font-arial;
    size: 18px;
    weight: bold;
  }
}
```

También podemos sacar dos clases más para poderlas reutilizar más adelante:

```
.size-container {
  width: 100%;
  height: 80px;
}

.letter-transform {
  text-transform: uppercase;
  letter-spacing: 5px;
}
```

Finalmente, nuestra clase `.header` quedaría:

```
.header {
  @extend .center;
  @extend .size-container;
  @extend .letter-transform;
  background-color: $green;
  color: $white;
  font: {
    family: $font-arial;
    size: 18px;
    weight: bold;
  }
}
```

## 9. Main Section 

* Imagen del mockup:

<img src="./readme-assets/main-section.png" alt="Main Section" />

* En el archivo HTML escribiremos lo siguiente:

```
<section class="main-section">
  <img src="./assets/main-image.png" alt="Main Image">
</section>
```

* En el archivo SCSS escribiremos lo siguiente:

```
```

## 10. Search Section

* Imagen del mockup:

<img src="./readme-assets/search.png" alt="Search" />

* En el archivo HTML escribiremos lo siguiente:

```
<section class="search-section">
  <div class="search-section-title">Search</div>
  <div class="search-section-input">
    <i class="fas fa-search"></i>
    <input type="text" placeholder="SEARCH YOUR ANIMAL">
  </div>
</section>
```

El ícono lo puedes sacar de Font Awesome y para ello debes copiar dentro de la etiqueta `<head>` de tu HTML el enlace que te muestra la siguiente documentación: https://fontawesome.com/start 

Y ya puedes escoger el ícono que más te guste aquí: https://fontawesome.com/icons?d=gallery

* En el archivo SCSS escribiremos lo siguiente:

```
.search-section {
  &-title {
    @extend .center;
    @extend .size-container;
    @extend .letter-transform;
    background-color: $green;
    color: $white;
    font: {
      family: $font-arial;
      size: 18px;
    }
  }
  &-input {
    background-color: $white;
    display: grid;
    grid-template-columns: 60px auto;
    justify-items: center;
    align-items: center;
    input {
      @extend .size-container;
      border: 0px;
      outline: none;
      font-size: 18px;
      letter-spacing: 5px;
    }
  }
}
```

## 11. Crab Section 

* Imagen del mockup:
* En el archivo HTML escribiremos lo siguiente:

```
```

* En el archivo SCSS escribiremos lo siguiente:

```
```

## 12. Cat Section

* Imagen del mockup:
* En el archivo HTML escribiremos lo siguiente:

```
```

* En el archivo SCSS escribiremos lo siguiente:

```
```

## 13. Footer 

* Imagen del mockup:

<img src="./readme-assets/footer.png" alt="Footer" />

* En el archivo HTML escribiremos lo siguiente:

```
<footer class="footer">
  <p>
    <span>Created by</span><br>@myuser
  </p>
</footer>
```

* En el archivo SCSS escribiremos lo siguiente:

```
.footer {
  @extend .center;
  @extend .size-container;
  @extend .letter-transform;
  background-color: $white;
  color: $pink;
  font: {
    size: 15px;
    weight: bold;
  }
  p {
    text-align: center;
    span {
      color: $green;
    }
  }
}
```