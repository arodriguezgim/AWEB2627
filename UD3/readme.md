# UD 3 - CSS Básico

---

## Índice de Contenidos

1. Introducción a CSS
2. Selectores CSS Básicos
3. Colores y Unidades de Medida
4. Tipografía y Texto
5. Fondos y Bordes
6. Modelo de Cajas (Box Model)
7. Display y Visibilidad
8. Posicionamiento Básico
9. Flexbox Básico
10. CSS Grid Básico
11. Responsive Design Básico
12. Pseudo-clases Básicas

---

## 1. Introducción a CSS

CSS (Cascading Style Sheets) es el lenguaje que se utiliza para dar estilo y presentación a documentos HTML.

### ¿Cómo aplicar CSS?

#### 1.1 CSS Inline (en línea)
```html
<p style="color: blue; font-size: 16px;">Texto azul</p>
```
❌ **No recomendado** - Mezcla contenido con presentación.

#### 1.2 CSS Interno (en el head)
```html
<!DOCTYPE html>
<html>
<head>
    <style>
        p {
            color: blue;
            font-size: 16px;
        }
    </style>
</head>
<body>
    <p>Texto azul</p>
</body>
</html>
```
⚠️ **Uso limitado** - Solo para páginas únicas.

#### 1.3 CSS Externo (archivo separado)
```html
<!-- index.html -->
<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" href="estilos.css">
</head>
<body>
    <p>Texto azul</p>
</body>
</html>
```

```css
/* estilos.css */
p {
    color: blue;
    font-size: 16px;
}
```
✅ **RECOMENDADO** - Separación de responsabilidades.

### Sintaxis básica de CSS

```css
selector {
    propiedad: valor;
    otra-propiedad: otro-valor;
}
```

---

## 2. Selectores CSS Básicos

Los selectores determinan qué elementos HTML serán estilizados.

### 2.1 Selectores principales

```css
/* Selector de elemento */
p {
    color: red;
}

/* Selector de clase */
.destacado {
    background-color: yellow;
}

/* Selector de ID */
#cabecera {
    font-size: 24px;
}
```

### 2.2 Combinando selectores

```css
/* Descendiente (todos los p dentro de div) */
div p {
    color: blue;
}

/* Agrupación de selectores */
h1, h2, h3 {
    font-family: Arial, sans-serif;
    color: #333;
}
```

### 2.3 Especificidad (¿Qué regla gana?)

Cuando hay conflicto entre reglas, gana la más específica:

1. **ID**: 100 puntos
2. **Clase**: 10 puntos  
3. **Elemento**: 1 punto

```css
/* Especificidad: 1 */
p { color: blue; }

/* Especificidad: 10 - ¡Esta gana! */
.texto { color: red; }

/* Especificidad: 100 - ¡Esta gana sobre todo! */
#principal { color: green; }
```

---

## 3. Colores y Unidades de Medida

### 3.1 Colores

```css
/* Nombres de colores */
color: red;

/* Hexadecimal */
color: #FF0000;
color: #F00; /* Forma corta */

/* RGB */
color: rgb(255, 0, 0);

/* RGBA (con transparencia) */
color: rgba(255, 0, 0, 0.5);

/* HSL (Tono, Saturación, Luminosidad) */
color: hsl(0, 100%, 50%);

/* HSLA (con transparencia) */
color: hsla(0, 100%, 50%, 0.5);
```

### 3.2 Unidades de medida

#### Unidades más comunes
```css
/* Píxeles (más común y fácil) */
font-size: 16px;
width: 300px;

/* Porcentaje */
width: 50%;

/* Em (relativo al tamaño de fuente del padre) */
font-size: 1.5em;
```

**Ejemplo práctico:**
```css
body {
    font-size: 16px; /* Base */
}

h1 {
    font-size: 32px; /* Título grande */
}

p {
    font-size: 16px; /* Texto normal */
}
```

---

## 4. Tipografía y Texto

### 4.1 Fuentes

```css
/* Familia de fuente */
font-family: Arial, Helvetica, sans-serif;

/* Tamaño */
font-size: 16px;

/* Peso (grosor) */
font-weight: normal; /* 400 */
font-weight: bold; /* 700 */
font-weight: 100; /* Thin */
font-weight: 900; /* Black */

/* Estilo */
font-style: normal;
font-style: italic;
font-style: oblique;

/* Variante */
font-variant: small-caps;

/* Shorthand (atajo) */
font: italic bold 16px/1.5 Arial, sans-serif;
/*     estilo peso tamaño/altura fuente */
```

### 4.2 Propiedades de texto

```css
/* Color del texto */
color: #333;

/* Alineación */
text-align: left;
text-align: center;
text-align: right;
text-align: justify;

/* Decoración */
text-decoration: none;
text-decoration: underline;
text-decoration: line-through;
text-decoration: overline;

/* Transformación */
text-transform: uppercase;
text-transform: lowercase;
text-transform: capitalize;

/* Espaciado entre letras */
letter-spacing: 2px;

/* Espaciado entre palabras */
word-spacing: 5px;

/* Altura de línea */
line-height: 1.5;
line-height: 24px;

/* Indentación */
text-indent: 30px;

/* Sombra de texto */
text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
/*           x   y   blur color */
```

### 4.3 Ejemplo básico con Google Fonts

```html
<!-- En el HTML -->
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700&display=swap" rel="stylesheet">
```

```css
/* En el CSS */
body {
    font-family: 'Roboto', sans-serif;
}
```

---

## 5. Fondos y Bordes

### 5.1 Fondos

```css
/* Color de fondo */
background-color: #f0f0f0;

/* Imagen de fondo */
background-image: url('imagen.jpg');

/* Repetición */
background-repeat: no-repeat;
background-repeat: repeat-x; /* Solo horizontal */
background-repeat: repeat-y; /* Solo vertical */

/* Posición */
background-position: center;
background-position: top right;
background-position: 50% 50%;
background-position: 10px 20px;

/* Tamaño */
background-size: cover; /* Cubre todo el contenedor */
background-size: contain; /* Se ajusta sin recortar */
background-size: 100% auto;

/* Fijo o con scroll */
background-attachment: fixed;
background-attachment: scroll;

/* Shorthand */
background: #333 url('bg.jpg') no-repeat center/cover;

/* Múltiples fondos */
background: 
    url('overlay.png') center/cover no-repeat,
    url('background.jpg') center/cover no-repeat;
```

### 5.2 Gradientes básicos

```css
/* Gradiente lineal */
background: linear-gradient(to right, red, blue);
background: linear-gradient(to bottom, #333, #666);
```

### 5.3 Bordes

```css
/* Ancho, estilo y color */
border-width: 2px;
border-style: solid;
border-color: black;

/* Shorthand */
border: 2px solid black;

/* Bordes individuales */
border-top: 1px solid red;
border-right: 2px dashed blue;
border-bottom: 3px dotted green;
border-left: 4px double orange;

/* Estilos de borde */
border-style: solid;
border-style: dashed;
border-style: dotted;
border-style: double;
border-style: groove;
border-style: ridge;
border-style: inset;
border-style: outset;

/* Bordes redondeados */
border-radius: 10px;
border-radius: 50%; /* Círculo */
border-radius: 10px 20px 30px 40px; /* sup-izq, sup-der, inf-der, inf-izq */
border-radius: 10px 20px; /* superior-izq/inferior-der, superior-der/inferior-izq */

/* Esquinas individuales */
border-top-left-radius: 10px;
border-top-right-radius: 20px;
border-bottom-right-radius: 30px;
border-bottom-left-radius: 40px;
```

### 5.4 Sombras

```css
/* Sombra de caja */
box-shadow: 5px 5px 10px rgba(0,0,0,0.3);
/*          x   y   blur spread color */

box-shadow: 0 4px 6px rgba(0,0,0,0.1);

/* Múltiples sombras */
box-shadow: 
    0 1px 3px rgba(0,0,0,0.12),
    0 1px 2px rgba(0,0,0,0.24);

/* Sombra interna */
box-shadow: inset 0 0 10px rgba(0,0,0,0.5);
```

---

## 6. Modelo de Cajas (Box Model)

Cada elemento HTML es una caja rectangular compuesta por:

```
┌─────────────────────────────────┐
│         MARGIN (exterior)       │
│  ┌───────────────────────────┐  │
│  │    BORDER (borde)         │  │
│  │  ┌─────────────────────┐  │  │
│  │  │  PADDING (relleno)  │  │  │
│  │  │  ┌───────────────┐  │  │  │
│  │  │  │   CONTENT     │  │  │  │
│  │  │  │  (contenido)  │  │  │  │
│  │  │  └───────────────┘  │  │  │
│  │  └─────────────────────┘  │  │
│  └───────────────────────────┘  │
└─────────────────────────────────┘
```

### 6.1 Propiedades del modelo de cajas

```css
.caja {
    /* Contenido */
    width: 300px;
    height: 200px;
    
    /* Padding (espacio interior) */
    padding: 20px; /* Todos los lados */
    padding: 10px 20px; /* vertical horizontal */
    padding: 10px 20px 30px 40px; /* top right bottom left */
    
    /* Propiedades individuales */
    padding-top: 10px;
    padding-right: 20px;
    padding-bottom: 30px;
    padding-left: 40px;
    
    /* Border */
    border: 2px solid black;
    
    /* Margin (espacio exterior) */
    margin: 20px;
    margin: 10px 20px;
    margin: 10px 20px 30px 40px;
    
    /* Propiedades individuales */
    margin-top: 10px;
    margin-right: 20px;
    margin-bottom: 30px;
    margin-left: 40px;
    
    /* Centrar horizontalmente */
    margin: 0 auto;
}
```

### 6.2 Box-sizing

Por defecto, width y height solo afectan al contenido:

```css
/* Comportamiento por defecto */
.caja1 {
    width: 300px;
    padding: 20px;
    border: 5px solid black;
    /* Ancho total = 300 + 40 + 10 = 350px */
}

/* Border-box: incluye padding y border en el width */
.caja2 {
    box-sizing: border-box;
    width: 300px;
    padding: 20px;
    border: 5px solid black;
    /* Ancho total = 300px */
}

/* Aplicar a todos los elementos (recomendado) */
* {
    box-sizing: border-box;
}
```

### 6.3 Overflow

Controla qué pasa cuando el contenido es más grande que el contenedor:

```css
.contenedor {
    width: 200px;
    height: 100px;
    
    overflow: visible; /* Por defecto, se desborda */
    overflow: hidden; /* Oculta el contenido que se desborda */
    overflow: scroll; /* Siempre muestra scrollbars */
    overflow: auto; /* Scrollbars solo si es necesario */
    
    /* Control individual */
    overflow-x: auto;
    overflow-y: hidden;
}
```

---

## 7. Display y Visibilidad

### 7.1 Propiedad Display

```css
/* Display: block */
.block {
    display: block;
    /* - Ocupa todo el ancho disponible
       - Empieza en nueva línea
       - Acepta width y height
       - Ejemplos: div, p, h1-h6 */
}

/* Display: inline */
.inline {
    display: inline;
    /* - Solo ocupa el espacio de su contenido
       - No empieza en nueva línea
       - NO acepta width y height
       - NO acepta margin/padding verticales
       - Ejemplos: span, a, strong */
}

/* Display: inline-block */
.inline-block {
    display: inline-block;
    /* - Combina ambos comportamientos
       - No empieza en nueva línea
       - SÍ acepta width y height
       - SÍ acepta margin y padding */
    width: 200px;
    height: 100px;
    margin: 10px;
}

/* Display: none */
.oculto {
    display: none;
    /* Elimina el elemento del flujo (no ocupa espacio) */
}

/* Display: flex */
.flex-container {
    display: flex;
    /* Activa Flexbox (ver sección 9) */
}

/* Display: grid */
.grid-container {
    display: grid;
    /* Activa Grid (ver sección 10) */
}
```

### 7.2 Visibilidad

```css
/* Visibility */
.invisible {
    visibility: hidden;
    /* Oculta el elemento pero SIGUE ocupando espacio */
}

.visible {
    visibility: visible;
}

/* Opacity */
.transparente {
    opacity: 0; /* Invisible */
    /* Valores de 0 (transparente) a 1 (opaco) */
}

.semi-transparente {
    opacity: 0.5;
}
```

**Diferencias importantes:**
- `display: none` → No ocupa espacio
- `visibility: hidden` → Sí ocupa espacio
- `opacity: 0` → Sí ocupa espacio y puede interactuar

---

## 8. Posicionamiento

### 8.1 Tipos de posicionamiento

```css
/* Static (por defecto) */
.static {
    position: static;
    /* Flujo normal del documento
       No responde a top, right, bottom, left */
}

/* Relative */
.relative {
    position: relative;
    top: 20px;
    left: 30px;
    /* Se desplaza RELATIVO a su posición original
       El espacio original se mantiene reservado */
}

/* Absolute */
.absolute {
    position: absolute;
    top: 0;
    right: 0;
    /* Se posiciona RELATIVO al ancestro posicionado más cercano
       Sale del flujo normal (no reserva espacio)
       Si no hay ancestro posicionado, se posiciona respecto al body */
}

/* Fixed */
.fixed {
    position: fixed;
    bottom: 20px;
    right: 20px;
    /* Se posiciona RELATIVO al viewport
       Permanece fijo al hacer scroll
       Sale del flujo normal */
}

/* Sticky */
.sticky {
    position: sticky;
    top: 0;
    /* Híbrido entre relative y fixed
       Se comporta como relative hasta que alcanza el offset
       Entonces se comporta como fixed */
}
```

### 8.2 Propiedades de posicionamiento

```css
.posicionado {
    position: absolute;
    
    /* Coordenadas */
    top: 10px;
    right: 20px;
    bottom: 30px;
    left: 40px;
    
    /* Z-index (capas, mayor número = más arriba) */
    z-index: 10;
    
    /* Solo funciona en elementos posicionados (no static) */
}
```

### 8.3 Ejemplo práctico: Centrar absolutamente

```css
.centrado-absoluto {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    /* Centra perfectamente el elemento */
}
```

### 8.4 Ejemplo: Menú fijo

```css
.menu-fijo {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    background: white;
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    z-index: 1000;
}

/* Compensar el espacio del menú fijo */
body {
    padding-top: 60px; /* Altura del menú */
}
```

---

## 9. Flexbox Básico

Flexbox es un sistema de layout que facilita la distribución de elementos en una dimensión (fila o columna).

### 9.1 Conceptos básicos

```css
.flex-container {
    display: flex;
    /* Convierte el elemento en flex container
       Los hijos directos se convierten en flex items */
}
```

### 9.2 Propiedades del contenedor (padre)

```css
.flex-container {
    display: flex;
    
    /* Dirección principal */
    flex-direction: row; /* Por defecto (horizontal) */
    flex-direction: column; /* Vertical */
    
    /* Alineación horizontal */
    justify-content: flex-start; /* Al inicio (por defecto) */
    justify-content: center; /* Al centro */
    justify-content: flex-end; /* Al final */
    justify-content: space-between; /* Espacio entre elementos */
    
    /* Alineación vertical */
    align-items: stretch; /* Estirar (por defecto) */
    align-items: flex-start; /* Arriba */
    align-items: center; /* Centro */
    align-items: flex-end; /* Abajo */
    
    /* Espaciado entre items */
    gap: 20px; /* Espacio entre elementos */
}
```

### 9.3 Propiedades de los elementos (hijos)

```css
.flex-item {
    /* Crecimiento (cuánto espacio extra toma) */
    flex-grow: 0; /* Por defecto (no crece) */
    flex-grow: 1; /* Crece para llenar espacio */
    
    /* Base */
    flex-basis: auto; /* Tamaño natural */
    flex-basis: 200px; /* Tamaño específico */
    
    /* Shorthand */
    flex: 1; /* Crece y llena el espacio disponible */
}
```

### 9.4 Ejemplos prácticos

#### Centrar contenido
```css
.centrar-todo {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
}
```

#### Layout de 3 columnas
```css
.columnas {
    display: flex;
    gap: 20px;
}

.columna {
    flex: 1; /* Todas ocupan el mismo espacio */
}
```

#### Barra de navegación
```css
.navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
}

.navbar-menu {
    display: flex;
    gap: 1rem;
    list-style: none;
}
```

---

[## 10. Grid Básico](./Grid/readme.md)

Grid es un sistema de layout que facilita la distribución de elementos en dos dimensiones (filas y columnas).

[Ejercicios de GRID](./Grid/Ejercicios/readme.md)

## 11. Responsive Design Básico

### 11.1 Viewport Meta Tag

```html
<!-- SIEMPRE incluir en el <head> -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### 11.2 Media Queries básicas

```css
/* Móviles pequeños */
@media (max-width: 576px) {
    .contenedor {
        padding: 10px;
    }
}

/* Móviles grandes / tablets pequeñas */
@media (min-width: 577px) and (max-width: 768px) {
    .contenedor {
        padding: 15px;
    }
}

/* Tablets */
@media (min-width: 769px) and (max-width: 992px) {
    .contenedor {
        padding: 20px;
    }
}

/* Escritorio */
@media (min-width: 993px) {
    .contenedor {
        padding: 30px;
    }
}
```

### 11.3 Breakpoints comunes

```css
/* Mobile First (diseño desde móvil hacia arriba) */
/* Por defecto: móvil */
.columna {
    width: 100%;
}

/* Tablets en adelante */
@media (min-width: 768px) {
    .columna {
        width: 50%;
    }
}

/* Desktop en adelante */
@media (min-width: 1024px) {
    .columna {
        width: 33.33%;
    }
}
```

### 11.4 Imágenes responsive

```css
img {
    max-width: 100%;
    height: auto;
    display: block;
}

/* Imágenes de fondo responsive */
.hero {
    background-image: url('hero-mobile.jpg');
    background-size: cover;
    background-position: center;
}

@media (min-width: 768px) {
    .hero {
        background-image: url('hero-tablet.jpg');
    }
}

@media (min-width: 1200px) {
    .hero {
        background-image: url('hero-desktop.jpg');
    }
}
```

### 11.5 Ejemplo completo: Layout responsive

```css
/* Mobile First */
.layout {
    display: flex;
    flex-direction: column;
    gap: 20px;
    padding: 15px;
}

.sidebar {
    order: 2; /* Sidebar después del main en móvil */
}

.main {
    order: 1;
}

/* Tablet */
@media (min-width: 768px) {
    .layout {
        padding: 30px;
    }
    
    .main {
        font-size: 18px;
    }
}

/* Desktop */
@media (min-width: 1024px) {
    .layout {
        flex-direction: row;
        max-width: 1200px;
        margin: 0 auto;
    }
    
    .sidebar {
        flex: 0 0 250px;
        order: 1; /* Sidebar a la izquierda */
    }
    
    .main {
        flex: 1;
        order: 2;
    }
}
```

---

## 12. Pseudo-clases Básicas

### 12.1 Pseudo-clases para enlaces

```css
/* Enlaces */
a:link { color: blue; } /* No visitado */
a:visited { color: purple; } /* Visitado */
a:hover { color: red; } /* Al pasar el ratón */
a:active { color: orange; } /* Al hacer clic */
```

### 12.2 Pseudo-clases para formularios

```css
/* Formularios */
input:focus {
    border-color: blue;
    outline: none;
}

input:disabled {
    background: #f0f0f0;
    cursor: not-allowed;
}

button:hover {
    background-color: #333;
}
```

### 12.3 Pseudo-clases de posición

```css
/* Posición */
li:first-child {
    /* Primer hijo */
    font-weight: bold;
}

li:last-child {
    /* Último hijo */
    border-bottom: none;
}

li:nth-child(2) {
    /* Segundo hijo */
}

li:nth-child(odd) {
    /* Hijos impares (1, 3, 5...) */
    background: #f0f0f0;
}

li:nth-child(even) {
    /* Hijos pares (2, 4, 6...) */
    background: white;
}
```

### 12.4 Ejemplos prácticos

#### Lista estilizada
```css
ul.custom-list {
    list-style: none;
    padding-left: 0;
}

ul.custom-list li:hover {
    background-color: #f5f5f5;
}
```

#### Botón interactivo
```css
.boton {
    background: #3498db;
    color: white;
    padding: 10px 20px;
    border: none;
    cursor: pointer;
}

.boton:hover {
    background: #2980b9;
}

.boton:active {
    background: #1f618d;
}
```

---

## Recursos adicionales

### Herramientas útiles

- **MDN Web Docs**: [developer.mozilla.org/es/docs/Web/CSS](https://developer.mozilla.org/es/docs/Web/CSS)
- **Can I Use**: [caniuse.com](https://caniuse.com) - Compatibilidad de navegadores
- **CSS-Tricks**: [css-tricks.com](https://css-tricks.com) - Tutoriales y guías
- **Flexbox Froggy**: [flexboxfroggy.com](https://flexboxfroggy.com) - Aprender Flexbox jugando
- **CSS Validation**: [jigsaw.w3.org/css-validator](https://jigsaw.w3.org/css-validator)

### Frameworks CSS básicos

- **Bootstrap**: Framework completo con componentes
- **Bulma**: Framework modular basado en Flexbox

---

## Ejercicios recomendados

1. **Básico**: Crear una tarjeta de perfil con imagen, nombre y descripción
2. **Intermedio**: Layout básico con header, main y footer usando Flexbox
3. **Intermedio**: Página de productos con tarjetas responsive
4. **Avanzado**: Página completa responsive con navegación y secciones
5. **Avanzado**: Sitio web personal con múltiples páginas

---

