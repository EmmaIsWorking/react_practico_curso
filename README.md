# React Course

## Index
- [React Course](#react-course)
  - [Index](#index)
  - [Dependencias:](#dependencias)
    - [React-dom](#react-dom)
    - [Webpack](#webpack)
    - [Webpack Dev Server](#webpack-dev-server)
    - [SASS](#sass)
    - [EsLint](#eslint)
    - [.gitignore](#gitignore)
    - [File Loader](#file-loader)
    - [Fake API](#fake-api)
  - [Content](#content)
  - [How to clone](#how-to-clone)
  - [Installation](#installation)
  - [Preview](#preview)
  - [Notes](#notes)
  - [Concepts](#concepts)
    - [Tipos de componentes:](#tipos-de-componentes)
      - [Stateful](#stateful)
      - [Stateless & Presentatitonal:](#stateless--presentatitonal)
    - [Props](#props)
    - [Metodos de Ciclos de Vida](#metodos-de-ciclos-de-vida)
      - [Montaje:](#montaje)
      - [Actualización:](#actualizaci%c3%b3n)
      - [Demonstaje:](#demonstaje)
      - [Manejo de errores](#manejo-de-errores)
    - [ESLint](#eslint-1)
    - [Añadiendo imágenes con Webpack](#a%c3%b1adiendo-im%c3%a1genes-con-webpack)
    - [Fake API](#fake-api-1)

## Dependencias:
### React-dom
`npm install react react-dom`

Instalación de Babel y otras herramientas para que funcione con React:

`npm install @babel/core babel-loader @babel/preset-env @babel/preset-react --save -dev`

Configuración de Babel (.babelrc):

```
{
  "presets": [
    "@babel/preset-env",
    "@babel/preset-react"
  ],
}
```
### Webpack
Webpack:
Instalación de Webpack y algunos plugins:

```
npm install webpack webpack-cli html-webpack-plugin html-loader  --save-dev

```

Configuración de Webpack (webpack.config.js):


```
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.js',
  },
  resolve: {
    extensions: ['.js', '.jsx'],
  },
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
        },
      },
      {
        test: /\.html$/,
        use: {
          loader: 'html-loader',
        },
      },
    ],
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: './public/index.html',
      filename: './index.html',
    }),
  ],
};
```

Script para ejecutar las tareas de Webpack (package.json):

```
{
  "scripts": {
    "build": "webpack --mode production"
  },
}

```
### Webpack Dev Server
Instalación de Webpack Dev Server:

`npm install --save-dev webpack-dev-server`

Script para ejecutar el servidor de Webpack y visualizar los cambios en tiempo real (package.json):

```
{
  "scripts": {
    "build": "webpack --mode production",
    "start": "webpack-dev-server --open --mode development"
  },
}
```


### SASS
Instalación de Sass:

`npm install --save-dev mini-css-extract-plugin css-loader node-sass sass-loader`

```
const MiniCssExtractPlugin = require('mini-css-extract-plugin');

// ...

module: {
  rules: [
    {
      test: /\.(s*)css$/,
      use: [
        { loader: MiniCssExtractPlugin.loader },
        'css-loader',
        'sass-loader',
      ],
    },
  ],
},

// ...

plugins: [
  new MiniCssExtractPlugin({
    filename: 'assets/[name].css',
  }),
],`
```

### EsLint
`npm install --save-dev eslint babel-eslint eslint-config-airbnb eslint-plugin-import eslint-plugin-react eslint-plugin-jsx-a11y`

[.eslintrc link](https://gist.github.com/EmmaIsWorking/1b22884691d3848b141c9cf35a6d6672)

### .gitignore
[.gitignore link](https://gist.github.com/EmmaIsWorking/1366317dcfcdc90c1801bece25cca0c6)

### File Loader
Instalación de File Loader:

`npm install --save-dev file-loader`

Configuración de File Loader en Webpack (webpack.config.js):

```
rules: [
  {
    test: /\.(png|gif|jpg)$/,
    use: [
      {
        loader: 'file-loader',
        options: { name: 'assets/[hash].[ext]' },
      }
    ],
  },
],
```

Uso de File Loader con React:

```
import React from 'react';
import nombreDeLaImagen from '../assets/static/nombre-del-archivo';

const Component = () => (
  <img src={nombreDeLaImagen} />
);

export default Component;
```

### Fake API
Instalación de JSON Server:
```
sudo npm install json-server -g
```

Recuerda que en Windows debes correr tu terminal de comandos en modo administrador.

Ejecutar el servidor de JSON Server:

```bash
json-server archivoParaTuAPI.json
```

`npx create-react-app @NameProyect`


## Content

- App
  - Header
  - Search
  - Categories
    - Carousel
      - CorouselItems
  - Footer

## How to clone
## Installation
## Preview
## Notes
## Concepts

### Tipos de componentes:
Los nombres de nuestros componentes deben empezar con una letra mayúscula, al igual que cada nueva palabra del componente. Esto lo conocemos como Pascal Case o Upper Camel Case.

#### Stateful
son los más robustos de React. Los usamos creando clases que extiendan de React.Component. Nos permiten manejar estado y ciclo de vida (más adelante los estudiaremos a profundidad).

#### Stateless & Presentatitonal:
También tenemos componentes Stateless o Presentacionales. Los usamos creando funciones que devuelvan código en formato JSX (del cual hablaremos en la próxima clase).

### Props
Las Props son la forma de enviar y recibir información en nuestros componentes.



### Metodos de Ciclos de Vida
Todos los componentes en React pasan por una serie de fases que generalmente se denominan “Ciclo de Vida del componente” es un proceso que React hace en cada componente, en algunos casos no podemos verlos como un bloque de código y en otros podemos llamarlos en nuestro componente para asignar una actividad según sea el caso necesario.

Los componentes en react pasan por un Montaje, Actualización, Desmontaje y Manejo de errores.

[¿Qué son los métodos del ciclo vida?](https://platzi.com/clases/1651-react-ejs/22576-que-son-los-metodos-del-ciclo-vida/)
#### Montaje:
`Constructor()`

`getDerivedStateFromProps()`

`render()`

`ComponentDidMount()`

#### Actualización:
`getDerivedStateFromProps()`

`shouldComponentUpdate()`

`render()`

`componentDidUpdate()`

#### Demonstaje:
`componentWillUnmount()`

#### Manejo de errores
`getDerivedStateFromError()`

### ESLint
Los linters como ESLint son herramientas que nos ayudan a seguir buenas prácticas o guías de estilo de nuestro código.
En algunos casos también pueden solucionar los errores automáticamente. De esta manera podemos solucionar los errores incluso antes de que sucedan.

Instalacion: [EsLint](#eslint)

### Añadiendo imágenes con Webpack

Vamos a usar File Loader para acceder a las imágenes de nuestro proyecto desde el código.

Inicialmente, estos archivos estáticos se encuentran junto al código de desarrollo. Pero al momento de compilar, Webpack guardará las imágenes en una nueva carpeta junto al código para producción y actualizará nuestros componentes (o donde sea que usemos las imágenes) con los nuevos nombres y rutas de los archivos.

[Instalacion Link](#file-loader)

### Fake API
Vamos a usar JSON Server para crear una Fake API: una API ““falsa”” construida a partir de un archivo JSON que nos permite preparar nuestro código para consumir una API de verdad en el futuro.

[Instalacion Link](#fake-api)